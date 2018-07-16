# utl_npl_star_trek_universal_language_translator_sort_of
NLP_Star Trek Universal Language Translator.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    NLP_Star Trek Universal Language Translator

    WPS Proc Python

    Translating from Spanish to English

    You do not need a google API key and google does not limit the use of its translators.

    github
    https://tinyurl.com/ycgk5rmd
    https://github.com/rogerjdeangelis/utl_npl_star_trek_universal_language_translator_sort_of

    stackoverflow
    https://tinyurl.com/yb68tgdx
    https://stackoverflow.com/questions/51340386/how-to-translate-word-with-google-translator

    Jackson Meister profile
    https://stackoverflow.com/users/925405/jacksonmeister

    SOAPBOX ON

    SAS/WPS is my base system but (base SAS is why)

    I find python the go to language for AI, Natural Language Processing, Raspberry PI, Arduino,
    smart homes, computer vision, sound processing ....

    R for in memory bleeding edge Stats and simutaneous row and column processing. I also
    like it for JSON/XML and HTML processing.

    It is a real pain converting data structures in Python and R, so
    that you can communicate with other languages.

    Google translator output data structure is inscrutable?

    SOAPBOX OFF


    INPUT
    =====

     SD1.HAVE total obs=6

           SPANISH

       donde esta usted
       buenas noches
       buenos dias
       donde creciste?
       otros idiomas
       universidad

     EXAMPLE OUTPUT
     --------------

      WANTWPS total obs=7

            E

       0 where are you?
       1 good night
       2 good day
       3 Where did you grow up?
       4 other languages
       5 university


    PROCESS ( Working Code)
    =======================

      translator = Translator();
      text = translator.translate(str(wantwps['SPANISH']), src='es', dest='en');


    OUTPUT
    ======

     SD1.WANTWPS total obs=7

        E

        0 where are you?
        1 good night
        2 good days
        3 Where did you grow up? '
        4 'other languages'
        5 b'university '
        Name: SPANISH, dtype: object

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
      input spanish & $64.;
    cards4;
    donde esta usted
    buenas noches
    buenos dias
    donde creciste?
    otros idiomas
    universidad
    ;;;;
    run;quit;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;
    * uses a file for converting ta traslator data structure to pandas dataframe;

    %utlfkil(d:/txt/output.txt);
    %utl_submit_wps64("
    options set=PYTHONHOME 'C:\Progra~1\Python~1.5\';
    options set=PYTHONPATH 'C:\Progra~1\Python~1.5\lib\';
    libname wrk  sas7bdat '%sysfunc(pathname(work))';
    libname sd1 'd:/sd1';
    proc python;
    submit;
    import numpy as np;
    import pandas as pandas;
    from sas7bdat import SAS7BDAT;
    from pandas import pandas;
    from googletrans import Translator;
    wantwps = pandas.read_sas('d:/sd1/have.sas7bdat');
    translator = Translator();
    text = translator.translate(str(wantwps['SPANISH']), src='es', dest='en');
    print(text.text, file=open('d:/txt/output.txt', 'a'));
    df = pandas.read_table('d:/txt/output.txt',header=None,names=('E'));
    endsubmit;
    import python=df data=wrk.wantwps;
    run;quit;
    ");

