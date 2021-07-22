# SasTipsTricks
Tips and tricks learned over 20+ years as a SAS/Microsoft consultant
# content

 - [Documentation](#documentation)

   - [Headers](#headers)

   - [Data Steps](#data-steps)

   - [Procs](#procs)

   - [Macro](#macro)

   - [Indentation](#indentation)

   - [Casing](#casing)

   - [Datalines4](#datalines4)

   - [IN Variables](#in-variables)

   - [ATTRIB Statement](#attrib-statement)

   - [DATEs/DATETIMEs](#datesdatetimes)
 
 - [Efficiencies](#efficiencies)

   - [Create a Sample for Testing](#create-a-sample-for-testing)

     - [Example 1 – You already have a small sample but want to test impact on larger sizes](#example-1--you-already-have-a-small-sample-but-want-to-test-impact-on-larger-sizes)

     - [Example 2 – You have a large dataset but want a fairly random sample to test](#example-2--you-have-a-large-dataset-but-want-a-fairly-random-sample-to-test)

     - [Example 3 – You want just something to test with without worrying about a random sample](#example-3--you-want-just-something-to-test-with-without-worrying-about-a-random-sample)

   - [Read a dataset ONCE](#read-a-dataset-once)

   - [Handle the data efficiently on the read](#handle-the-data-efficiently-on-the-read)

     - [Example 1](#example-1)

     - [Example 2](#example-2)

   - [Drop/Keep Variables](#dropkeep-variables)

   - [Views](#views)

   - [PROC SQL vs Data Step/Sort](#proc-sql-vs-data-stepsort)

   - [Limit column sizes](#limit-column-sizes)

   - [Careful on numerics vs chars](#careful-on-numerics-vs-chars)

   - [OPTIONS COMPRESS=YES](#options-compressyes)

   - [Pass-Through SQL / Implicit Pass-Through](#passthrough-sql--implicit-passthrough)

   - [Indexing](#indexing)

   - [SASFILE Statement](#sasfile-statement)

   - [MEMLIB system option](#memlib-system-option)

   - [Working with Dates and Datetimes](#working-with-dates-and-datetimes)

   - [OPEN=DEFER](#opendefer)

   - [Formats](#formats)

     - [Format catalogs](#format-catalogs)

     - [Lookup Tables](#lookup-tables)

   - [Change the current working directory](#change-the-current-working-directory)

   - [Hide the DB passwords](#hide-the-db-passwords)

   - [PROC SUMMARY](#proc-summary)

     - [Multiple OUTPUTS:](#multiple-outputs)

     - [CHARTYPE AND WHERE Clauses](#chartype-and-where-clauses)

 - [Dynamic Code](#dynamic-code)

   - [SAS Dictionary library](#sas-dictionary-library)

   - [PUT Statements vs Macros](#put-statements-vs-macros)

 - [Write to the List vs the Log](#write-to-the-list-vs-the-log)

 - [Use a dataset as a lookup in another dataset](#use-a-dataset-as-a-lookup-in-another-dataset)

 - [Macros](#macros)

   - [Scope](#scope)

   - [Check if dataset exists](#check-if-dataset-exists)
   - [Save macros ](#save-macros)

 - [Other](#other)

   - [Read the logs](#read-the-logs)

   - [Save the logs](#save-the-logs)

   - [Set all WARNINGs as ERRORs](#set-all-warnings-as-errors)

   - [Licensed and Installed](#licensed-and-installed)

 - [Connect via ODBC](#connect-via-odbc)

 - [Resources](#resources)

   - [SAS-L](#sasl)

   - [PROC-X.com](#procxcom)

   - [SAS Consulting Forum (Google Groups)](#sas-consulting-forum-google-groups)

   - [SAS Forums](#sas-forums)

 - [Command-Line Submission](#commandline-submission)

   - [Overview](#overview)

   - [Steps](#steps)

   - [Screenshots](#screenshots)

 - [Autoexec Standardization](#autoexec-standardization)

     - [Usage](#usage)

 - [Advanced Concepts](#advanced-concepts)

   - [_N_](#_N_)

   - [Hash Objects](#hash-objects)

     - [Simple example ( direct from Paul Dorfman’s paper. See Appendix: References)](#simple-example--direct-from-paul-dorfmans-paper-see-appendix-references)

   - [Bit Flags](#bit-flags)

   - [Submitting Jobs in Parallel](#submitting-jobs-in-parallel)

     - [Overview](#overview)

     - [Sample Code](#sample-code)

     - [Unix](#unix)

     - [Windows](#windows)

  - [PROC HTTP](#proc-http)

 - [Appendix: Tips](#appendix-tips)

   - [Software Suggestions](#software-suggestions)

   - [Sample FCMP](#sample-fcmp)

 - [Appendix: Useful Commands](#appendix-useful-commands)

   - [List of all active options](#list-of-all-active-options)

 - [Appendix: References](#appendix-references)

   - [PDV](#pdv)

   - [Indexing](#indexing)

   - [Hash Object](#hash-object)

# Documentation

## Headers

All production programs should include a standard header. While there are many variations of headers, I recommend using one that will result in automatic tool documentation. The following header will result in the ability to automatically generate documentation. **Notice the need for a semicolon at the end of each statement (even if it runs multiple lines).**
```
    /*---------------------------------------------------------------------------*
     Company    : Savian ;
     Location   : Colorado Springs, CO 80906 ;
     Author     : Alan Churchill ;
     Program    : Read NMON data ;
     Support    : alan.churchill@savian.net ;
     SAS Version: SAS 9.13 ;
     Description: This program reads in documents for SaviDoc.;
     Usage      : Fill in the appropriate macro parameters listed below.;
     Remarks    : NMON data consists of several sources in 1 file.;
     Event      : alchur, 05Mar2012, Initial coding. ;
    *---------------------------------------------------------------------------*/
```
## Data Steps

```
   /*---------------------------------------------------------------------------*
   DataStep   : AAA ;
   Description: The AAA section is generated by NMON at the start of the data
                collection and contains information about the system and NMON
                itself – contents vary by release following is for 12e;
   Input      : AAA;
   Output     : AAA;
   SeeAlso    : http://en.wikipedia.org/wiki/Nmon ;
   *---------------------------------------------------------------------------*/
```

## Procs

<div>

<pre>    /*---------------------------------------------------------------------------*
    Proc       : SORT ;
    Description: Sorts the NMON JSF information for merging;
    Input      : AAA;
    Output     : AAA;
    SeeAlso    : http://en.wikipedia.org/wiki/Nmon ;
    *---------------------------------------------------------------------------*/
    </pre>

</div>

## Macro

<div>

<pre>    /*---------------------------------------------------------------------------*
    Macro      : Example ;
    Description: This is the macro description ;
    Parm       : Parm1 - This is parm1 description, Default=parm1Default ;
    Parm       : Parm2 - This is parm2 description ;
    Example    : %Example(parm1=NorthWind2,parm2=employee2);
    SeeAlso    : http://www.sascommunity.org.com/ ;
    *---------------------------------------------------------------------------*/
    </pre>

</div>

## Indentation

Code should be indented where it is logical. This makes it far easier to maintain and read. For example, the following would be considered well formatted code:

<div>

<pre>    data Test ;
       set SasHelp.Class;
       if x = 1 then
          do;
             x = x + 2;
          end;
    run;
    </pre>

</div>

## Casing

Variable name casing should be consistent. There are numerous types of casing but here is a suggested framework:

*   Variable names should be Camel cased
*   DataSet names should be Pascal cased

Camel case states that the first word is all lower case and then each subsequent word is upper-cased on the first letter and lower-cased for all subsequent letters. For example:

<pre>    myvariablename becomes myVariableName
</pre>

## Datalines4

DATALINES4 should be used in place of DATALINES/CARDS/PARMCARDS. It allows for a semi-colon in the data w/o blowing up. It is terminated with 4 semi-colons and was built to withstand semi-colons in the raw data.

<div>

<pre>        data test;
           input name $;
        datalines4;
        Alan
        Chris
        Bobby
        Greg
        TEAM;
        ;;;;
        run;
    </pre>

</div>

## IN Variables

For IN variables in merges, name it so it is logical when reading the action. For example, here is how merges are commonly done:

<div>

<pre>        data Test ;
        merge EzBday (in=a)
              Universe (in=b);
           by postalCode;
        if a=1 and b=1;
        run;
    </pre>

</div>

Use the following instead:

<div>

<pre>        data Test ;
           merge EzBday (in=inEzBday)
                 Universe (in=inUniverse);
              by postalCode;
        if inEzBday and inUniverse;
        run;
    </pre>

</div>

## ATTRIB Statement

The ATRIB statement should be used in place of format or length statements because it is more versatile and is easier to change and add at a later point:

<div>

<pre>        data test ;
           attrib myVar length=$20 format=$20\. label=”This is my variable”
                  ;
        …
        run;
    </pre>

</div>

## DATEs/DATETIMEs  

**SAS does NOT have any notion of a date or datetime variable type: that is very important to understand.** What you perceive as a date is the number of days since Jan 1, 1960 (SAS epochal date). Datetime is number of seconds. All systems have epochal dates. Unix is Jan 1, 1970, Microsoft is Jan 1, 1900, Mac is slightly weird (1904), SQL Server has one in the 1700s, etc. That allows adding/subtracting of dates. Same way the Mayans did it (history trivia here).  

- When you format a date, you merely put a mask on it for viewing. An informat deciphers a mask and converts the perceived date to a number representing the number of days since Jan 1, 1960 (plus or minus). A format displays it. **IN**format vs format. Hence, 24 is a date to SAS. So is 6000\. What you choose to display to the user is a date format. Sept 22, 2020 is a number to SAS (see below). If you want to add 2 dates, you can. Any arithmetic with dates works. Want to add a day to a datetime? Sure, 86400 seconds in a day. Add it to a ‘datetime’ in SAS and it works. Here, SAS shows what the value is for today:

<pre>    data _null_;
       x = **'22SEP2020'd**;
       put x=;
    run;
</pre>

x=22180 NOTE: DATA statement used (Total process time):

# Efficiencies

**The number one issue with SAS is how many records are read/written, how many columns, and what are in those columns. This is known as I/O. With SAS, always focus on reducing the I/O.** How to do that is the emphasis of this section.

## Create a Sample for Testing

**Always, always, always test against a sample of large data** . There are numerous ways to do this.

### Example 1 – You already have a small sample but want to test impact on larger sizes

<div>

<pre>        data test;
           set sashelp.shoes;
           do i = 1 to 100 ;
              output ;
           end;
        run;
    </pre>

</div>

### Example 2 – You have a large dataset but want a fairly random sample to test

Ok, this one uses a mathematical function call MOD (abbreviated as %). Per SAS: “<a name="a000844703"></a>The MOD function returns the remainder from the division of argument-1 by argument-2.”. Hence, if we use a mod of _n_ and the ‘amount’ we want (every 100<sup>th</sup> record), we can use mod(_n_,100). Let’s see it in action:

<div>

<pre>        data test;
           set largeData;
           if mod(_n_,100) then
              output ;
        run;
    </pre>

</div>

### Example 3 – You want just something to test with without worrying about a random sample

<div>

<pre>        data test;
           set largeData;
           if _n_ < 101 ;
        run;
    </pre>

</div>

## Read a dataset ONCE

One of the most common mistakes made by SAS programmers is reading large datasets multiple times. Wherever possible, read a dataset (especially large ones) once. If you need to break it up into pieces for further processing do that. Here is an example of a single read:

<div>

<pre>        data Test1
             Test2
             Test3
             Test4
             ;
           set sashelp.class;
           select;
              when (age<12)
                 do;
                    rank=1;
                    output Test1;
                 end;
              when (age<13)
                 do ;
                    rank=2;
                    output Test2;
                 end;
              when (age<14)
                 do ;
                    rank=3;
                    output Test3;
                 end;
              otherwise
                 do ;
                    rank=4;
                    output Test4;
                 end;
           end;
        run;
    </pre>

</div>

SELECT statements are particularly useful for this purpose since they are a cascading filter. A record will only match 1 of the WHEN statements so it is an easy to use bucketing system. Try and do whatever manipulation is needed for a record in the when clause before it is output to the new dataset:

<div>

<pre>        when (age<14)
           do ;
              rank = 1;
              newName = substr(name,1,3);
              if (lowcase(newName) = “joh” then
                  category=”Johnson”;
           end;
    </pre>

</div>

## Handle the data efficiently on the read

### Example 1

Too many programmers do not consider the system impact on the initial read. This is a critical area for efficiency. For example:

<div>

<pre>        data test (keep=age);
           set reallyLargeData;
           age = substr(demogr,1,2);
        run;
    </pre>

</div>

In this example, the age variable is the only variable read and the only variable retained on the write. Assume, for this example, that the dataset reallyLargeData contains dozens of variables. A better way to handle this scenario would be:

<div>

<pre>        data test (keep=age);
           set reallyLargeData (keep=demogr);
           age = substr(demogr,1,2);
        run;
    </pre>

</div>

This reduces the size of the data coming in and therefore reduces the processing per record.

### Example 2

<div>

<pre>        data test;
           set reallyLargeData;
           if age > 10 ;
        run;
    </pre>

</div>

A better way to handle this is:

<div>

<pre>        data test;
           set reallyLargeData(where=(age>10));
        run;
    </pre>

</div>

Use a WHERE clause instead of a subsetting if where possible. The where clause keeps the data from coming into the PDV whereas the IF statement requires the whole record to be read in first before evaluation.

## Drop/Keep Variables

Make sure you always drop unnecessary variables. This is a major cause of slow processing time and the easiest thing to correct. Especially in work datasets that simply do not need them:

<div>

<pre>        data test (drop=age lastName firstName);
    </pre>

</div>

## Views

Views are one of the least used options by many SAS programmers. However, they allow for incredible gains in processing speed and allow for a lot of flexibility. **Views should be used on a regular basis by most SAS programmers.** Common SAS code:

<div>

<pre>        data test;
           set reallyLargeData;
           if age > 10 then
              rank = 1;
           else
              rank = 2;
        run;

        proc sort data=test;
           by rank;
        run;
    </pre>

</div>

The above represents 2 steps and reads the data twice. A better way to handle this is by using a VIEW and it has no impact on the data step functionality/flexibility:

<div>

<pre>        data test / view=test;
           set reallyLargeData;
           if age > 10 then
              rank = 1;
           else
              rank = 2;
        run;

        proc sort data=test;
           by rank;
        run;
    </pre>

</div>

It is even possible to pass a view through certain PROCs. This is an undocumented feature raised in a SGF paper in 2011 and formally discussed by SAS for 9.4M6 ([Paper](https://www.lexjansen.com/wuss/2011/coders/Papers_Billings_T_73653.pdf)):

<div>

<pre>				data _null_ / view=v_out;
				   length sex $ 1 _FREQ_ Height_Min Height_Max 8;
				   set v_out;
				   put _all_;
				run;

				proc means data=sashelp.class noprint;
				   class sex;
				   var Height;
				   ways 1;
				   output out=v_out(drop=_TYPE_) min= max= / autoname;
				run;
    </pre>

</div>

## PROC SQL vs Data Step/Sort

Proc SQL allows for numerous steps to happen at the same time. Oftentimes, this can replace the data read of several steps with a single pass of the data. However, the data step is far more flexible in how it handles data. Combine them using a view:

<div>

<pre>        data class / view=class;
            set sashelp.class;
            if age > 12 then
               rank = 1;
            else
               rank = 2;
            run;

            proc sql ;
               create table test2 as
               select rank, sex, sum(height), sum(weight)
               from class
               group by rank, sex
               order by rank
               ;
            quit;
    </pre>

</div>

## Limit column sizes

For character columns, consider using lengths to limit what is needed:

<div>

<pre>        attrib notes length=$60 ;
    </pre>

</div>

## Careful on numerics vs chars

Here is a simple statement that seems innocuous: flag = “1” ; However, by using a character variable vs a numeric, the actual overhead for this processing is multiples larger than a numeric. It is better to use a numeric in all cases vs using a character: flag = 1; (See [Advanced: Bit Flags](https://d.docs.live.net/8bca55fbca813d37/Private/Alan/my%20documents/SAS%20Tips%20Tricks.docx#_Bit_Flags) section for an even more advanced means of handling)

## OPTIONS COMPRESS=YES

Using the compress=yes option in SAS can oftentimes result in tremendous processing savings…but not always. It depends on the data. If you have a lot of character fields with space in the field, compress can buy a lot of process time savings and disk space savings. However, if your data is a lot of short character fields/numeric fields, compress-yes can cost you across the board. Always review your logs to look for examples of compression hurting performance. Compression in SAS is not the same as compression in a utility such as zip or rar. SAS compression changes the structure of how data is stored within a SAS dataset but keeps the data the same. A utility such as zip actually makes the data smaller where it can.

## Pass-Through SQL / Implicit Pass-Through

A SAS SQL query going against an RDBMS will try and craft its query so that it uses pass-through SQL vs bringing the data local to SAS and processing the data in SAS: this is known as implicit pass-through. The performance differences between having the DBMS do the process and bringing the data back to SAS for processing can be enormous. As much as possible, a SAS programmer should strive to have the DBMS handle the load. By setting the options, a programmer can see in the log whether SAS used pass-through processing:

<div>

<pre>        options sastrace=’,,,d’;
    </pre>

</div>

Generally, if a SAS proc SQL query is fairly simply, without complex function calls, SAS will be able to craft the query and pass it to the DBMS for pass-through processing. Checking the logs will tell you whether this happened. A guaranteed way to ensure the DBMS handles the processing is to use explicit pass-through code:

<div>

<pre> 
    	proc sql;
         connect to oracle as myconn (user=smith password=secret path='myoracleserver');
         select *
         from connection to myconn
            (select empid, lastname, firstname, salary
             from employees
             where salary>75000);
         disconnect from myconn;
      quit;
    </pre>

</div>

## Indexing

Indexing a dataset cost time and disk space to create the index. However, if using a dataset on a regular basis with where clause subsetting, indexing can provide record level access very quickly:

<div>

<pre>        proc datasets library=cdsales;
            modify bighits;
            index create cdnumber / unique;
            run;
    </pre>

</div>

Using an index:

<div>

<pre>        data cdsales;
            set olddata.oldhits;
            where cdnumber eq “123456” and artistname eq “Led Zeppelin”;
            … more SAS Statements…
            run;
    </pre>

</div>

**_Note: Due to the complexity of indexes, Please see the appendix at the end of this document for more detail on how to use an index._**

## SASFILE Statement

The SASFILE statement can be used for datasets that are accessed on a regular basis. The statement forces a dataset up into memory. However, the loading time for the dataset can be significant so it should only be used for datasets that are frequently accessed. Here is a sample showing the load of a dataset:

<div>

<pre>        data work.shoes;
           set sashelp.shoes;
        run;

        SASFILE work.shoes open;

        proc reg data= work.shoes;
           ....
        run;

        **** work.shoes stays in memory until you close it **;**
        SASFILE work.shoes close;

</pre>

</div>

## MEMLIB system option

Using MEMLIB will push the SAS work library into memory.

## Working with Dates and Datetimes

A SAS date and a SAS datetime are both simply numbers. A date operates as the number of days since Jan 1, 1960 and a datetime is the number of seconds since Jan 1, 1960 at midnight. This Jan 1, 1960 date is known as the ‘epochal’ date. This convention of using a date fixed in time to measure from is very common. Unix uses Jan 1, 1970 and some Microsoft products use Jan 1, 1900 while others use Jan 1, 1980. Because dates and datetimes are simply numbers, converting back and forth is easy using simple mathematics. For example, to convert from a datetime to a date is: newDate = oldDateTime / 86400 ; 86400 being the number of seconds in a day. Similarly, you can convert to a datetime from a date using the reverse: newDateTime = oldDate * 86400 ; SAS also provides functions for doing this conversion but I find the mathematics easier to use and it is faster for the CPU.

## OPEN=DEFER

If you have a number of datasets having the same name, consider using OPEN=DEFER: SET DATA_2018: open=defer; It is a wildcard setting to help read data.

## Formats

### Format catalogs

Format catalogs are almost always a bad idea. Why? They are tied to not only the operating system they were created on but also the ‘bitness’ of that O/S. Hence, if the source for the formats is lost, it is almost impossible to recreate. A better alternative is %include or table-driven formats. Even table-driven formats are a challenge. Using a data step and put statements, you can achieve a generated proc format w/o having any odd dependencies. Create a table of values, generate the SAS code, %include it as needed. Regen formats as much as needed. Maintainability is key to everything in the coding world.

### Lookup Tables

Formats can be used for lookup tables (as a simpler alternative to hash for smaller datasets). Formats are an in-memory mechanism and can be extremely fast. Generally, you don’t want to load a table more than a couple of hundred thousand in size but it is relatively easy to create a format from a dataset:

<div>

<pre>        data format;
            set Adm.luOccasion (rename=(occasionId=start occasionName=label)) end=last ;
            retain fmtname 'Occasion' type 'n' ;
            output ;
            if last then
               do;
                  hlo='O';
                  label='Other';
                  output;
               end;
            run;

            proc format cntlin=format ;
            run;
    </pre>

</div>

## Change the current working directory

<pre>    data _null_;
       rc=dlgcdir("c:**\t**emp");
       put rc=;
    run;
</pre>

## Hide the DB passwords

<pre>    proc pwencode in="abc123";
    run;

    Log file: {SAS002}3CD4EA1E5C9B75D91A73A37F
    libname mydblib oracle path=airdb_remote schema=hrdept
    user=myusr1 password="{SAS002}3CD4EA1E5C9B75D91A73A37F ";
</pre>

## PROC SUMMARY

### Multiple OUTPUTS:

<div>

<pre>         proc summary data=Trans nway missing;
            class LOB;
            var sales;
            output out=Auto(where=(LOB='Auto') drop=_FREQ_ _TYPE_) sum=AutoSales;
            output out=SB (where=(LOB='Small') drop=_FREQ_ _TYPE_) sum=SBSales;
            output out=Comm (where=(LOB='Comm')) drop=_FREQ_ _TYPE_) sum=CommSales;
         quit;
    </pre>

</div>

### CHARTYPE AND WHERE Clauses

CHARTYPE option allows proc summary to output a string that indicates what the crossing is of each class variable. With this, you can efficiently manage multiple summaries to their own datasets:

<div>

<pre>        proc summary data=sashelp.shoes missing chartype;
            class region product subsidiary;
            var sales;
            output out=RegionProduct (where=(_TYPE_='110') drop=_FREQ_) sum=;
            output out=RegionSub (where=(_TYPE_='101') drop=_FREQ_) sum=;
            output out=ProductSub (where=(_TYPE_='011') drop=_FREQ_) sum=;
        run;
    </pre>

</div>

# Dynamic Code

## SAS Dictionary library

SAS has a DICTIONARY library that is automatically created but not visible. It allows for the investigation of metadata within SAS. Here is a simple example:

<div>

<pre>        PROC SQL;
            CREATE TABLE DICT AS
               SELECT *
               FROM DICTIONARY.COLUMNS
               WHERE UPCASE(LIBNAME)='SASHELP' AND
               UPCASE(MEMNAME)='SHOES'
            ;
        QUIT;
    </pre>

</div>

More information can be found here: [https://support.sas.com/documentation/cdl/en/sqlproc/62086/HTML/default/viewer.htm#a001385596.htm](https://support.sas.com/documentation/cdl/en/sqlproc/62086/HTML/default/viewer.htm#a001385596.htm)

## PUT Statements vs Macros

Macros can get to be very hard to debug. Hence, it is often better to use a put/include solution to coding. The dictionary tables combined with the use of PUT/INFILE method statements will often lead to dynamic coding:

<div>

<pre>        * USE WHEN NOT DEBUGGING CODE: ;
            * filename TEMP '$MYTEMPFILE';
            * USE WHEN DEBUGGING CODE: ;
            filename TEMP 'c:\temp\Test.sas';

            data _null_ ;
               file TEMP ;
               set DICT end=eof;
               if _n_ = 1 then
                  do ;
                     put 'data Africa ; '
                       / ' attrib '
                       ;
                  end;
               if label = "" then
                  put @12 name @30 'label="XX_' name +(-1) '"' ;
               else
                  put @12 name @30 'label="XX_' label +(-1)'"' ;
               if eof then
                  do ;
                     put @12';'
                          / ' set sashelp.SHOES;'
                          / 'run;'
                          ;
                  end;
            run;

            %include TEMP ;
    </pre>

</div>

# Write to the List vs the Log

It is possible to write to the list output vs the log:

<div>

<pre>        options pagesize=60 linesize=64 nodate pageno=1;
        title 'Leading Grain Producers';
        title2 'for 1996';

        data _null_;
           set grain_producers;
           file print header=newpage;
           where year=1996;
           format country $cntry.;
           label type='Grain';
           put country @25 type @50 kilotons;
           return;

           newpage:
              put 'Country' @25 'Grain' @50 'Kilotons';
              put 60*'=';
              return;
        run;
    </pre>

</div>

# Use a dataset as a lookup in another dataset

<div>

<pre>        data Medical;
           set Physical (rename=(Patient=tmpPatient));
           do i=1 to nobs;
              set Drugs nobs=nobs point=i;
              if Patient=tmpPatient then output;
           end;
        run;
    </pre>

</div>

# Macros

Never use stored compiled macros. Always use autocall libraries (or %INCLUDES). The autocall feature came after the compiled macro facility. There is virtually no gain, performance-wise, with pre-compiling and can actually increase the time since autocall only compiles what it needs. Additionally, you can lose the source, the code is not protected from prying eyes (it can be read in a hex editor), and it is not portable across operating systems. As of SAS 9.4M5, a %IF macro call can be used in open code vs only in a macro.

## Scope

Tip from macro guru: _However, as a macro instructor, what I tell students in every class I teach is that every macro should explicitly specify whether a macro variable should be local or global. Counting on the environment to make the right decision regarding where to store a macro variable or where to retrieve it from is a bad idea._ _In this particular case, since the logic to assign the value may never be reached, I would suggest a better approach would be to have a %local statement at the top of the program that defines it as local and a %let statement before the data step that assigns an appropriate default value._

## Check if dataset exists

<pre>    %if %sysfunc(exist(&lib..&table.)) %then %do; %end;
    %else %goto macroexit;
    %put Made It;
    Alt:
    %if not %sysfunc(exist(&lib..&table.)) %then %do; %end;
    %else %goto macroexit;
    %put Made It;
</pre>

## Save work data to perm location
	
<pre>
libname permdata v9 'c:\temp';
proc copy in=work out=permdata memtype=data;
run;
[Thanks to KSharp on SAS Community]
</pre>
	
## Save macros 

	From SAS website:
	
	/* Place the GLOBAL macro variable(s) into a permanent SAS data set.  */ 

	libname test ".";

	data test.vars;                                                                                                                             
	   set sashelp.vmacro(where=(scope='GLOBAL'));                                                                                         
	run;                                                                                                                                   

	/* Submit the following in a subsequent SAS session:  */

	libname test ".";

	/* Place the macro variable(s) back into the GLOBAL symbol table. */
	data _null_;                                                                                                                           
	   set test.vars(where=(scope='GLOBAL'));                                                                                                   
	   if substr(name,1,3) ne 'SYS' then do;                                                                                               
	      call execute('%global '||strip(name)||';');                                                                                   
	      call execute('%let '||strip(name)||'='||strip(value)||';');                                                             
	   end;                                                                                                                                 
	run;   


# Other

## Read the logs

For most jobs, especially those deployed in production, read the logs. A job may come back error free but the warnings and notes will tell a complete story. Look for the same data being read multiple times, numeric-character conversions, translation steps (v9 to SPDS conversion), etc.

## Save the logs

The SAS DMS window can easily overflow with log data. Avoid that by saving the log to an alternate location. Also, turn off the ods results viewer window:

<div>

<pre>      	ods results=off;
      	filename outFile = 'c:\temp\sasCodeRun.log';

        proc printto log=outFile print=outFile new;
        run;
        ods results=on;
    </pre>

</div>

Turn it off once done so the log returns to the DMS window:

<div>

<pre>        proc printto; run;
    </pre>

</div>

## Set all WARNINGs as ERRORs

Set options dsoptions=note2err so that all WARNINGs are errors.

<pre>    options dsoptions=note2err;
    data a;
       y=x;
    run;

    ERROR: Variable x is uninitialized.
</pre>

## Licensed and Installed

<pre>    *show licensed;
    proc setinit;run;

    *show installed;
    proc product_status;run;
</pre>

# Connect via ODBC

libname SQLREF ODBC NOPROMPT="server=SVDSQLDCP01;driver=ODBC Driver 13 for SQL Server;trusted_connection=yes;database=DEVAPP10_Shredding" STRINGDATES=NO IGNORE_READ_ONLY_COLUMNS=YES SCHEMA=DBO; Create a file on the Windows desktop and name it anything (test.txt, for example). Change the extension to .UDL and it will become an entry point for the Windows data link. Get the ODBC connection working there. Once working, open that file with a text editor and the connection needed will be written in that file.

# Resources

## SAS-L

There is a long-standing Usenet group known as SAS-L where users can post questions and get answers. It can be found here: [http://listserv.uga.edu/archives/sas-l.html](http://listserv.uga.edu/archives/sas-l.html)

## PROC-X.com

This is a blog aggregator and can be subscribed to. It provides a synopsis of the SAS blogs out there so you can pick and choose which blogs to visit vs. trying to keep up with all of them. [http://proc-x.com/](http://proc-x.com/)

## SAS Consulting Forum (Google Groups)

The SAS Consulting Forum is designed for much more complex subjects such as SAS BI administration, OLAP cube management, DS2, etc. It is a regulated forum so members must be approved to be on it. SAS R&D participates as well. [http://sasconsulting.google.com](http://sasconsulting.google.com/)

## SAS Forums

These are forums run by SAS itself and can be great sources of information on specialized areas such as EG: [https://communities.sas.com/welcome](https://communities.sas.com/welcome)

# Command-Line Submission

## Overview

SAS can be submitted via a command-line interface vs using an interactive tool such as EG. This is often much more useful and allows a SAS user to control the SAS options as well as keep their machine from being locked up while a long-running job is processing.

## Steps

*   Log onto the Unix host desired

· Create a SAS program to submit. For example, call it sasjob.sas · Create a shell program in a text editor (ex. Ultraedit). For example, call it sasjob.sh o Here are example contents:

<div>

'/sas913/SAS_9.1/sas' '/home/myuserid/code/TestLoggingImpact.sas' -log '/home/ myuserid /logs/TestLoggingImpact.log' -noovp -dmsbatch -noterminal -fullstimer -memsize 20G

</div>

Note: An additional option for autoexec can be added as well:

<div>

-autoexec ‘/home/myuserid/code/autoexec.sas’

</div>

· FTP the programs to the Unix server or, even easier, use the built in feature of UltraEdit to save the file to an ftp location.

*   On the command line, run the code:

<div>

sh sasjob.sh

</div>

· If you want to get back to the prompt, you can run the code in the background using an ‘&’:

<div>

sh sasjob.sh &

</div>

· Finally, if using UltraEdit, use the Open from FTP to retrieve the log or simply ftp the log back locally.

## Screenshots

In UltraEdit, File è FTP/Telnet è

# Autoexec Standardization

The following are standard options:

<div>

<pre>        options byerr;
            options cleanup;
            options compress=no;
            options datastmtchk=allkeywords;
            options details;
            options dkricond=error;
            options errorcheck=normal;
            options errors=5;
            options fmterr;
            options fullstimer;
            options mergenoby=error;
            options merror ;
            options mlogic;
            options mlogicnest ;
            options mprint;
            options mprintnest;
            options msglevel=I;
            options mstored;
            options serror ;
            options sortdup=logical;
            options sortequals;
            options source2;
            options source;
            options validvarname=v7;
            options vnferr;
    </pre>

</div>

### Usage

For command line, to use the above autoexec options, or to add more/modify them, create a new file called autoexec.sas and simple call it on the command-line: From our example:

<div>

<pre>        '/sas913/SAS_9.1/sas' '/users/myuserid/code/TestLoggingImpact.sas'
        -autoexec ‘/users/myuserid/code/autoexec.sas’ -log '/users/ myuserid
        /logs/TestLoggingImpact.log' -noovp -dmsbatch -noterminal -fullstimer
        -memsize 20G
    </pre>

</div>

# Advanced Concepts

## _N_

[From user posting online] It is worth noting that _n_ is not the observation number (although it often matches the observation number in many DATA steps).  It is actually a counter, counting the number of times that the programming logic has left the DATA statement in order to execute the remaining statements within the DATA step.  Understanding _n_ requires a solid understanding of how DATA steps work.

## Hash Objects

**[2020 NOTE: SAS is deemphasizing DS2 and it has no path forward. It is not recommended at this time.]** Hash objects are part of the DS2 language in SAS. They are an extension of the data step. Hash objects can dramatically improve performance of some SAS programs. However, they can also be detrimental if not used properly. Generally speaking, a hash object works best when a small table needs to be merged against a larger table. The time taken to load the hash table into memory is the key constraint along with having enough memory to do the hash. The below is a simple example of a match-merge using a hash object with resources linking to more comprehensive reading on the subject.

### Simple example ( direct from Paul Dorfman’s paper. See Appendix: References)

<div>

<pre>        data match ;
           set small point = _n_ ; * get key/data attributes for parameter type matching ;
           dcl hash hh (dataset: 'work.small', hashexp: 10) ;
              hh.DefineKey ( 'key' ) ;
              hh.DefineData ( 's_sat' ) ;
              hh.DefineDone () ;
              do until ( eof2 ) ;
                 set large end = eof2 ;
                 if hh.find () = 0 then output ;
              end ;
          stop ;
       run ;
    </pre>

</div>

In this match-merge example, 2 datasets are being merged: small and large. The small dataset is loaded into a hash table. Note: no sorting is needed prior to the match-merge. The small dataset is then matched with the large dataset on the variable ‘key’.

## Bit Flags

You should never use a character variable as a flag. The default char length is 8 which equates to 64 bits (8 bits * 8 bytes). A bit can be used for flagging since it represents 2 states: on/off. This doesn't matter at low volumes but it becomes critical at high volumes. Use bit flagging instead. Bit flagging is a trick but a useful one. Here is an example of bit flagging: Say we want to flag 4 items in an array. Well, we need an array of 4 bits: 0000 4 bits can hold a maximum value of 15 (1111) in decimal. Initialize the bits as a flag:

<div>

<pre>        data test;
           flags = 0 ; <=== binary is 0000
        run;

        Say we want to turn on flag 3:
        data test;
           flags = 4 ; <=== binary is 0100
        run;

        Say we want to turn on flag 1 and 3:
        data test;
           flags = 5 ; <=== binary is 0101
        run;

        Say we want to turn on flags 1, 3, and 4:
        data test;
           flags = 1 ; <=== binary is 0001
           flags + 4 ; <=== binary is 0101
           flags + 8 ; <=== binary is 1101
        run;
    </pre>

</div>

Bit flagging can also be used for more than 2 states by simply combining the bits values. 2 bits can represent 4 states (2 states * 2 bits).

## Submitting Jobs in Parallel

### Overview

SAS jobs can be submitted in parallel to break up large batch jobs. This technique takes advantage of the SYSTASK command built into Base SAS. There are slight variations between Unix and Windows so examples of both can be found here. For both samples, we will work with a simple program designed to stress the system slightly and run for a bit. Macros are not used simply to illustrate the concept.

### Sample Code

We will be using the following code as a sample. Whether it is test1.sas or test2.sas, it is executing this code. Adjust to fit your needs:

<div>

<pre>        %let loops=40000;
        data test;
           set sashelp.shoes;
           do i=1 to &loops;
              output;
           end;
        run;

        proc summary nway data=test;
           class region;
           var sales;
           output out=test mean= ;
        run;
    </pre>

</div>

### Unix

<div>

<pre>        data _null_ ;
            file "/users/_sasuser_/code/ParallelSample/test1.sh" ;
            put "'/sas913/SAS_9.1/sas' -sysin '/users/_sasuser_
        /code/ParallelSample/Test1.sas' -log '/users/_sasuser_
        /logs/Test1.log'";
            file "/users/_sasuser_ /code/ParallelSample/test2.sh" ;
            put "'/sas913/SAS_9.1/sas' -sysin
        '/users/sasuser/code/ParallelSample/Test2.sas' -log
        '/home/achurc1/logs/Test2.log'";
            run;
            systask kill chmod1 chmod2;
            systask command "chmod a+x /users/sasuser/code/ParallelSample/test1.sh
        &" taskname=chmod1;
            systask command "chmod a+x /users/sasuser/code/ParallelSample/test2.sh
        &" taskname=chmod2;
            waitfor _all_ chmod1 chmod2;
            systask kill test1 test2;
            systask command "sh /users/sasuser/code/ParallelSample/test1.sh"
        taskname=test1;
            systask command "sh /users/sasuser/code/ParallelSample/test2.sh"
        taskname=test2;
            waitfor _all_ test1 test2;
    </pre>

</div>

### Windows

<div>

<pre>        options noxwait noxsync;
            %let sasexe_options = -nosplash ;
            data _null_ ;
            file "c:\temp\test1.cmd" ;
            put "sas -sysin 'c:\temp\test1.sas' -nosplash -log
        'c:\temp\test1.log'";
            file "c:\temp\test2.cmd" ;
            put "sas -sysin 'c:\temp\test2.sas' -nosplash -log
        'c:\temp\test2.log'";
            run;
            systask kill test1 test2;
            systask command "c:\temp\test1.cmd" taskname=test1;
            systask command "c:\temp\test2.cmd" taskname=test2;
            waitfor _all_ test1 test2;
    </pre>

</div>

### PROC HTTP

<pre>
	/*===================================================
	| USAGE: OPERATIONAL CURL
	| -----------------------------------------------------
	|
	| curl --location --request POST 'http://localhost:9003/Email/SendEmailAsync?toAddresses=first.last%40gmail.com&subject=TestEmail' \
	| --header 'accept: text/plain' \
	| --header 'Content-Type: multipart/form-data' \
	| --form 'files=@"/E:/temp/message.html"' \
	| --form 'files=@"/E:/temp/report.xlsx"'
	*====================================================*/

	filename xcl "E:\temp\report.xlsx";
	filename input "E:\temp\message.html";
	filename debug "e:\temp\SasHttp.txt";

	proc http 
	   url="http://server01:9003/Email/SendEmailAsync"
	   query = ("toAddresses"="first.last@gmail.com"
		    "subject"="SAS Email")
	   headerout=debug
	   method="POST"
	   in = multi FORM ( "message.html" = input header="Content-Type: text/html",
			     "report.xlsx" = xcl header="Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
			   );  
	   * DEBUG LEVEL=3;
	run;

</pre>
	
# Appendix: Tips

## Software Suggestions

1.  Path Copy Copy Allows for context menu integration of copying full path of file
2.  BeyondCompare (portable version) Allows for difference checking of files
3.  Notepad++ (Portable version) For editors, I prefer UltraEdit and they have SAS modules for it.
4.  RegexBuddy (for regex testing and learning)

## Sample FCMP

<pre>  
   /*==========================================================
    FUNCTION: CM
    PURPOSE : Does a comparison of strings stripping out spaces and upcasing
    USAGE : isMatch=CM("string1","string2");
    *==========================================================*/
    function CM(p1$,p2$);
       if upcase(strip(p1)) = upcase(strip(p2)) then
          return (1);
       else
          return (0);
    endsub;
</pre>

# Appendix: Useful Commands

## List of all active options

<pre>    proc options internal;
    run;

    PROC SETINIT NOALIAS; RUN;
    PROC PRODUCT_STATUS; RUN;
</pre>

# Appendix: References

## PDV

30+ years old and still a great paper on how things work under the covers with SAS. MUST READ. [http://www.lexjansen.com/nesug/nesug88/SAS_supervisor.pdf](http://www.lexjansen.com/nesug/nesug88/SAS_supervisor.pdf)

## Indexing

[http://www2.sas.com/proceedings/sugi30/247-30.pdf](http://www2.sas.com/proceedings/sugi30/247-30.pdf)

## Hash Object

[http://www2.sas.com/proceedings/sugi30/236-30.pdf](http://www2.sas.com/proceedings/sugi30/236-30.pdf)
