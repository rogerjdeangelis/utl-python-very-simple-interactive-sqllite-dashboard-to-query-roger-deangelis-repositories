# utl-python-very-simple-interactive-sqllite-dashboard-to-query-roger-deangelis-repositories
    %let pgm=utl-python-very-simple-interactive-sqllite-dashboard-to-query-roger-deangelis-repositories;

    Very simple interactive sqllite dashboard to query roger deangelis repositories

        OVERVIEW

           INPUT (you only need to do this once)

             1 Create a sqllite relational database
             2 create sqllite table repos with one column containg a list of rogers 2,125 repository links

           PROCESS

             3 Create a tkinter dasboard textbox
             4 Enter your search string in the textbox
             5 Apply and close the textbox
             6 Pass text to sql query
             7 Execute the query

       TWO SOLUTIONS

             1 GUI dashboard
             2 Manual edit of python code
             3 Python dropdowns macros on end

    If you want to download a list of my 02FEB2024 repos (not necessary)
    http://tinyurl.com/2bay5xt5
    https://raw.githubusercontent.com/rogerjdeangelis/utl-python-very-simple-interactive-sqllite-dashboard-to-query-roger-deangelis-repositories/main/rogerjdeangelisrepos20240201.txt

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*      INPUT                                              SAMPLE OUTPUT (SAMPLE AI REPOS NOT ALL)                        */
    /*                                                                                                                        */
    /* Dashboard TextBox                                                                                                      */
    /*                                                                                                                        */
    /* Input put 'AI' in the text box                                                                                         */
    /* then hit the Apply button and                                                                                          */
    /* finally close with the X button    https://github.com/rogerjdeangelis/utl-AI-first-name-and-birth-date-range-to-gender */
    /*                                    https://github.com/rogerjdeangelis/utl-AI-geometry-is-the-figure-a-right-triangle-  */
    /* +-------------------------------+  https://github.com/rogerjdeangelis/utl_where_is_waldo_classic_computer_vision       */
    /* | Tk                     - [] X |  https://github.com/rogerjdeangelis/utl-AI-remove-noise-from-an-image-python-opencv  */
    /* +-------------------------------+  https://github.com/rogerjdeangelis/utl-python-AI-color-frequencies-in-an-image      */
    /* |AI                             |  https://github.com/rogerjdeangelis/utl_AI_is_it_a_license_plate                     */
    /* +-------------------------------+  ...                                                                                 */
    /* |           +------+            |                                                                                      */
    /* |           | Apply|            |                                                                                      */
    /* |           +------+            |                                                                                      */
    /* +-------------------------------+                                                                                      */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    /*----                                                                   ----*/
    /*----  1. Delete entire sqllite databas if it exists                    ----*/
    /*----  2. Create sqlite3 relational database                            ----*/
    /*----  3. Load table repositories in sqlite database                    ----*/
    /*----  4. Print the sql code that created the table                     ----*/
    /*----  5. You only have to create and database and load table once      ----*/
    /*--                                                                     ----*/

    %utl_pybegin;
    parmcards4;
    import os
    import sqlite3
    import pandas as pd
    repos = pd.read_csv("http://tinyurl.com/2bay5xt5",header=0)
    repos.info()
    os.remove("c:/temp/xport.db")
    database = "c:/temp/xport.db"
    mydb = sqlite3.connect(database)
    cur = mydb.cursor()
    cur.execute("drop table if exists repos")
    repos.to_sql(name="repos", con=mydb)
    repos=pd.read_sql_query("""select * from repos""",mydb)
    print("repos",repos)
    cur.execute("select * from sqlite_master")
    print("meta",cur.fetchall())
    mydb.close()
    ;;;;
    run;quit;
    %utl_pyend;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  PANDA DATAFRAME                                                                                                       */
    /*                                                                                                                        */
    /*  <class 'pandas.core.frame.DataFrame'>                                                                                 */
    /*  RangeIndex: 2,121 entries, 0 to 2,121                                                                                 */
    /*  Data columns (total 1 columns):                                                                                       */
    /*   #   Column  Non-Null Count  Dtype                                                                                    */
    /*  ---  ------  --------------  -----                                                                                    */
    /*   0   repos   1974 non-null   object                                                                                   */
    /*  dtypes: object(1)                                                                                                     */
    /*  memory usage: 15.5+ KB                                                                                                */
    /*                                                                                                                        */
    /*                                                                                                                        */
    /*  SQLLITE RELATIONAL TABLE REPOS                                                                                        */
    /*                                                                                                                        */
    /*  repos  index  repos                                                                                                   */
    /*  0         0  https://github.com/abkp5201209/rogerjdeangelis5                                                          */
    /*  1         1  https://github.com/kangweiding1s3/rogerjdeange...                                                        */
    /*  2         2  https://github.com/rogerjdeangelis/-let-pgm-ut...                                                        */
    /*  3         3  https://github.com/rogerjdeangelis/-utl-is-the...                                                        */
    /*  4         4  https://github.com/rogerjdeangelis/Calculate-m...                                                        */
    /*  ...     ...                                                ...                                                        */
    /*  1969   1969  https://github.com/rogerjdeangelis/utl_wps_sas...                                                        */
    /*  1970   1970  https://github.com/rogerjdeangelis/utl_xml_to_sas                                                        */
    /*  1971   1971  https://github.com/rogerjdeangelis/utlfind-fla...                                                        */
    /*  1972   1972          https://github.com/rogerjdeangelis/voodoo                                                        */
    /*  1973   1973  https://github.com/rogerjdeangelis/zip-and-unz...                                                        */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*               _       _           _     _                         _
    / |   __ _ _   _(_)   __| | __ _ ___| |__ | |__   ___   __ _ _ __ __| |
    | |  / _` | | | | |  / _` |/ _` / __| `_ \| `_ \ / _ \ / _` | `__/ _` |
    | | | (_| | |_| | | | (_| | (_| \__ \ | | | |_) | (_) | (_| | | | (_| |
    |_|  \__, |\__,_|_|  \__,_|\__,_|___/_| |_|_.__/ \___/ \__,_|_|  \__,_|
         |___/
    */

    /*----                                                                   ----*/
    /*---- Configure and execute tkinter dashboard textbox                   ----*/
    /*---- Enter search string apply and close                               ----*/
    /*---- Connect to sqllite relational database                            ----*/
    /*---- Connect to sqllite relational database c:/temp/xport.db           ----*/
    /*---- Pass search string to sql quer                                    ----*/
    /*---- Exccute query                                                     ----*/
    /*----                                                                   ----*/

    %utl_pybegin;
    parmcards4;
    from tkinter import *
    import sqlite3
    import pandas as pd
    from tabulate import tabulate
    root=Tk()
    def retrieve_input():
        global inputValue
        inputValue=textBox.get("1.0","end-1c")
        print(inputValue)
        return inputValue
    textBox=Text(root, height=1, width=44)
    textBox.pack()
    textBox.insert(END, "")
    buttonCommit=Button(root, height=1, width=10, text="Apply",command=lambda: retrieve_input())
    buttonCommit.pack()
    mainloop()
    print("done",inputValue)
    database = "c:/temp/xport.db"
    mydb = sqlite3.connect(database)
    cur = mydb.cursor()
    sql="""select repos from repos where instr(repos,?) > 0 """
    df=pd.read_sql_query(sql,mydb,params=[inputValue])
    print(tabulate(df, showindex=False, headers=df.columns))
    mydb.close()
    ;;;;
    run;quit;
    %utl_pyend;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* OUTPUT                                                                                                                 */
    /*                                                                                                                        */
    /* https://github.com/rogerjdeangelis/utl-AI-compute-the-distance-between-objects-in-an-image-python                      */
    /* https://github.com/rogerjdeangelis/utl-AI-first-name-and-birth-date-range-to-gender                                    */
    /* https://github.com/rogerjdeangelis/utl-AI-geometry-is-the-figure-a-right-triangle-                                     */
    /* https://github.com/rogerjdeangelis/utl-AI-internal-angles-of-polygon-from-vertex-coordinates-in-r                      */
    /* https://github.com/rogerjdeangelis/utl-AI-labeling-centroids-inside-and-within-a-boundary-polygon                      */
    /* https://github.com/rogerjdeangelis/utl-AI-remove-noise-from-an-image-python-opencv                                     */
    /* https://github.com/rogerjdeangelis/utl-AI-spelling-corrector-when-word-is-close-to-the-correct-word                    */
    /* https://github.com/rogerjdeangelis/utl-R-AI-igraph-list-connections-in-a-non-directed-graph-for-a-subset-of-vertices   */
    /* https://github.com/rogerjdeangelis/utl-adding-text-to-an-existing-png-graphic-python-AI                                */
    /* https://github.com/rogerjdeangelis/utl-area-of-intersection-of-arbitrary-polygons-R-AI                                 */
    /* https://github.com/rogerjdeangelis/utl-ascii-art-outline-maps-of-states-and-countries-AI                               */
    /* https://github.com/rogerjdeangelis/utl-capturing-old-faithful-before-and-during-an-eruption--AI-visual-analytics       */
    /* https://github.com/rogerjdeangelis/utl-how-many-triangles-in-the-polygon-r-igraph-AI                                   */
    /* https://github.com/rogerjdeangelis/utl-length-of-longest-common-word-in-two-sentences-text-AI                          */
    /* https://github.com/rogerjdeangelis/utl-python-AI-color-frequencies-in-an-image                                         */
    /* https://github.com/rogerjdeangelis/utl-shortest-and-longest-travel-time-from-home-to-work-igraph-AI                    */
    /* https://github.com/rogerjdeangelis/utl-using-image-variances-to-identify-goatee-man-image-processing-AI                */
    /* https://github.com/rogerjdeangelis/utl_AI_extracting_and_saving_video_frames                                           */
    /* https://github.com/rogerjdeangelis/utl_AI_is_it_a_license_plate                                                        */
    /* https://github.com/rogerjdeangelis/utl_AI_minimum_distance_from_a_poin_to_a_polygon                                    */
    /* https://github.com/rogerjdeangelis/utl_where_is_waldo_classic_computer_vision                                          */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
                                                                                           _   _                                 _
    /*___    __  __                         _            _ _ _            __   _ __  _   _| |_| |__   ___  _ __     ___ ___   __| | ___
    |___ \  |  \/  | __ _ _ __  _   _  __ _| |   ___  __| (_) |_    ___  / _| | `_ \| | | | __| `_ \ / _ \| `_ \   / __/ _ \ / _` |/ _ \
      __) | | |\/| |/ _` | `_ \| | | |/ _` | |  / _ \/ _` | | __|  / _ \| |_  | |_) | |_| | |_| | | | (_) | | | | | (_| (_) | (_| |  __/
     / __/  | |  | | (_| | | | | |_| | (_| | | |  __/ (_| | | |_  | (_) |  _| | .__/ \__, |\__|_| |_|\___/|_| |_|  \___\___/ \__,_|\___|
    |_____| |_|  |_|\__,_|_| |_|\__,_|\__,_|_|  \___|\__,_|_|\__|  \___/|_|   |_|    |___/

    */

    /*----  1. Edit the where cluase chage A1 to your search string          ----*/
    /*----  2. Query sqllite repositories table                              ----*/
    /*----  3. Query sqllite repositories table                              ----*/
    /*----  4. List repositories that contain the string                     ----*/
    /*----                                                                   ----*/

    %utl_pybegin;
    parmcards4;
    import sqlite3
    import pandas as pd
    database = "c:/temp/xport.db"
    mydb = sqlite3.connect(database)
    cur = mydb.cursor()
    df=pd.read_sql_query("""select repos from repos where instr(repos,'AI') > 0 """,mydb)
    from tabulate import tabulate
    print(tabulate(df, showindex=False, headers=df.columns))
    mydb.close()
    ;;;;
    run;quit;
    %utl_pyend;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* OUTPUT                                                                                                                 */
    /*                                                                                                                        */
    /* https://github.com/rogerjdeangelis/utl-AI-compute-the-distance-between-objects-in-an-image-python                      */
    /* https://github.com/rogerjdeangelis/utl-AI-first-name-and-birth-date-range-to-gender                                    */
    /* https://github.com/rogerjdeangelis/utl-AI-geometry-is-the-figure-a-right-triangle-                                     */
    /* https://github.com/rogerjdeangelis/utl-AI-internal-angles-of-polygon-from-vertex-coordinates-in-r                      */
    /* https://github.com/rogerjdeangelis/utl-AI-labeling-centroids-inside-and-within-a-boundary-polygon                      */
    /* https://github.com/rogerjdeangelis/utl-AI-remove-noise-from-an-image-python-opencv                                     */
    /* https://github.com/rogerjdeangelis/utl-AI-spelling-corrector-when-word-is-close-to-the-correct-word                    */
    /* https://github.com/rogerjdeangelis/utl-R-AI-igraph-list-connections-in-a-non-directed-graph-for-a-subset-of-vertices   */
    /* https://github.com/rogerjdeangelis/utl-adding-text-to-an-existing-png-graphic-python-AI                                */
    /* https://github.com/rogerjdeangelis/utl-area-of-intersection-of-arbitrary-polygons-R-AI                                 */
    /* https://github.com/rogerjdeangelis/utl-ascii-art-outline-maps-of-states-and-countries-AI                               */
    /* https://github.com/rogerjdeangelis/utl-capturing-old-faithful-before-and-during-an-eruption--AI-visual-analytics       */
    /* https://github.com/rogerjdeangelis/utl-how-many-triangles-in-the-polygon-r-igraph-AI                                   */
    /* https://github.com/rogerjdeangelis/utl-length-of-longest-common-word-in-two-sentences-text-AI                          */
    /* https://github.com/rogerjdeangelis/utl-python-AI-color-frequencies-in-an-image                                         */
    /* https://github.com/rogerjdeangelis/utl-shortest-and-longest-travel-time-from-home-to-work-igraph-AI                    */
    /* https://github.com/rogerjdeangelis/utl-using-image-variances-to-identify-goatee-man-image-processing-AI                */
    /* https://github.com/rogerjdeangelis/utl_AI_extracting_and_saving_video_frames                                           */
    /* https://github.com/rogerjdeangelis/utl_AI_is_it_a_license_plate                                                        */
    /* https://github.com/rogerjdeangelis/utl_AI_minimum_distance_from_a_poin_to_a_polygon                                    */
    /* https://github.com/rogerjdeangelis/utl_where_is_waldo_classic_computer_vision                                          */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*____
    |___ /   _ __ ___   __ _  ___ _ __ ___  ___
      |_ \  | `_ ` _ \ / _` |/ __| `__/ _ \/ __|
     ___) | | | | | | | (_| | (__| | | (_) \__ \
    |____/  |_| |_| |_|\__,_|\___|_|  \___/|___/

    */
    %macro utl_pybegin;
    %utlfkil(c:/temp/py_pgm.py);
    %utlfkil(c:/temp/py_pgm.log);
    filename ft15f001 "c:/temp/py_pgm.py";
    %mend utl_pybegin;

    %macro utl_pyend;
    run;quit;
    * EXECUTE THE PYTHON PROGRAM;
    options noxwait noxsync;
    filename rut pipe  "d:\Python310\python.exe c:/temp/py_pgm.py 2> c:/temp/py_pgm.log";
    run;quit;
    data _null_;
      file print;
      infile rut;
      input;
      put _infile_;
      putlog _infile_;
    run;quit;
    data _null_;
      infile " c:/temp/py_pgm.log";
      input;
      putlog _infile_;
    run;quit;
    %mend utl_pyend;


    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */

