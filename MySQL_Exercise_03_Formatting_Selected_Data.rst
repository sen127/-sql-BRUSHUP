
Copyright Jana Schaich Borg/Attribution-NonCommercial 4.0 International
(CC BY-NC 4.0)

MySQL Exercise 3: Formatting Selected Data
==========================================

In this lesson, we are going to learn about three SQL clauses or
functionalities that will help you format and edit the output of your
queries. We will also learn how to export the results of your formatted
queries to a text file so that you can analyze them in other software
packages such as Tableau or Excel.

**Begin by loading the SQL library into Jupyter, connecting to the
Dognition database, and setting Dognition as the default database.**

.. code:: python

    %load_ext sql
    %sql mysql://studentuser:studentpw@mysqlserver/dognitiondb
    %sql USE dognitiondb

.. code:: ipython3

    %load_ext sql
    %sql mysql://studentuser:studentpw@mysqlserver/dognitiondb
    %sql USE dognitiondb


.. parsed-literal::

    0 rows affected.




.. parsed-literal::

    []



1. Use AS to change the titles of the columns in your output
------------------------------------------------------------

The AS clause allows you to assign an alias (a temporary name) to a
table or a column in a table. Aliases can be useful for increasing the
readability of queries, for abbreviating long names, and for changing
column titles in query outputs. To implement the AS clause, include it
in your query code immediately after the column or table you want to
rename. For example, if you wanted to change the name of the time stamp
field of the completed\_tests table from "created\_at" to "time\_stamp"
in your output, you could take advantage of the AS clause and execute
the following query:

.. code:: mysql

    SELECT dog_guid, created_at AS time_stamp
    FROM complete_tests

Note that if you use an alias that includes a space, the alias must be
surrounded in quotes:

.. code:: mysql

    SELECT dog_guid, created_at AS "time stamp"
    FROM complete_tests

You could also make an alias for a table:

.. code:: mysql

    SELECT dog_guid, created_at AS "time stamp"
    FROM complete_tests AS tests

Since aliases are strings, again, MySQL accepts both double and single
quotation marks, but some database systems only accept single quotation
marks. It is good practice to avoid using SQL keywords in your aliases,
but if you have to use an SQL keyword in your alias for some reason, the
string must be enclosed in backticks instead of quotation marks.

**Question 1: How would you change the title of the "start\_time" field
in the exam\_answers table to "exam start time" in a query output? Try
it below:**

.. code:: ipython3

    %%sql 
    SELECT start_time AS "exam start time"
    FROM exam_answers
    LIMIT 100;


.. parsed-literal::

    100 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>exam start time</th>
        </tr>
        <tr>
            <td>2013-02-05 03:58:13</td>
        </tr>
        <tr>
            <td>2013-02-05 03:58:31</td>
        </tr>
        <tr>
            <td>2013-02-05 03:59:03</td>
        </tr>
        <tr>
            <td>2013-02-05 03:59:10</td>
        </tr>
        <tr>
            <td>2013-02-05 03:59:22</td>
        </tr>
        <tr>
            <td>2013-02-05 03:59:36</td>
        </tr>
        <tr>
            <td>2013-02-05 03:59:41</td>
        </tr>
        <tr>
            <td>2013-02-05 04:00:00</td>
        </tr>
        <tr>
            <td>2013-02-05 04:00:16</td>
        </tr>
        <tr>
            <td>2013-02-05 04:00:35</td>
        </tr>
        <tr>
            <td>2013-02-05 04:00:46</td>
        </tr>
        <tr>
            <td>2013-02-05 04:00:54</td>
        </tr>
        <tr>
            <td>2013-02-05 04:01:01</td>
        </tr>
        <tr>
            <td>2013-02-05 04:01:15</td>
        </tr>
        <tr>
            <td>2013-02-05 04:01:40</td>
        </tr>
        <tr>
            <td>2013-02-05 04:02:02</td>
        </tr>
        <tr>
            <td>2013-02-05 04:02:30</td>
        </tr>
        <tr>
            <td>2013-02-05 04:03:00</td>
        </tr>
        <tr>
            <td>2013-02-05 04:03:29</td>
        </tr>
        <tr>
            <td>2013-02-05 04:03:37</td>
        </tr>
        <tr>
            <td>2013-02-05 04:03:48</td>
        </tr>
        <tr>
            <td>2013-02-05 04:03:56</td>
        </tr>
        <tr>
            <td>2013-02-05 04:04:07</td>
        </tr>
        <tr>
            <td>2013-02-05 04:05:31</td>
        </tr>
        <tr>
            <td>2013-02-05 04:05:47</td>
        </tr>
        <tr>
            <td>2013-02-05 04:05:57</td>
        </tr>
        <tr>
            <td>2013-02-05 04:06:06</td>
        </tr>
        <tr>
            <td>2013-02-05 04:06:30</td>
        </tr>
        <tr>
            <td>2013-02-05 04:07:38</td>
        </tr>
        <tr>
            <td>2013-02-05 04:08:58</td>
        </tr>
        <tr>
            <td>2013-02-05 04:09:05</td>
        </tr>
        <tr>
            <td>2013-02-05 04:09:40</td>
        </tr>
        <tr>
            <td>2013-02-05 04:09:44</td>
        </tr>
        <tr>
            <td>2013-02-05 04:10:03</td>
        </tr>
        <tr>
            <td>2013-02-05 04:10:11</td>
        </tr>
        <tr>
            <td>2013-02-05 04:10:16</td>
        </tr>
        <tr>
            <td>2013-02-05 04:10:26</td>
        </tr>
        <tr>
            <td>2013-02-05 04:11:12</td>
        </tr>
        <tr>
            <td>2013-02-05 04:11:21</td>
        </tr>
        <tr>
            <td>2013-02-05 04:11:34</td>
        </tr>
        <tr>
            <td>2013-02-05 04:11:40</td>
        </tr>
        <tr>
            <td>2013-02-05 04:11:54</td>
        </tr>
        <tr>
            <td>2013-02-05 04:12:20</td>
        </tr>
        <tr>
            <td>2013-02-05 04:12:28</td>
        </tr>
        <tr>
            <td>2013-02-05 04:12:49</td>
        </tr>
        <tr>
            <td>2013-02-05 04:13:05</td>
        </tr>
        <tr>
            <td>2013-02-05 04:13:14</td>
        </tr>
        <tr>
            <td>2013-02-05 04:13:30</td>
        </tr>
        <tr>
            <td>2013-02-05 04:13:55</td>
        </tr>
        <tr>
            <td>2013-02-05 04:14:02</td>
        </tr>
        <tr>
            <td>2013-02-05 04:14:14</td>
        </tr>
        <tr>
            <td>2013-02-05 04:14:22</td>
        </tr>
        <tr>
            <td>2013-02-05 04:14:40</td>
        </tr>
        <tr>
            <td>2013-02-05 04:15:04</td>
        </tr>
        <tr>
            <td>2013-02-05 04:15:10</td>
        </tr>
        <tr>
            <td>2013-02-05 04:15:38</td>
        </tr>
        <tr>
            <td>2013-02-05 04:15:56</td>
        </tr>
        <tr>
            <td>2013-02-05 04:16:02</td>
        </tr>
        <tr>
            <td>2013-02-05 04:16:18</td>
        </tr>
        <tr>
            <td>2013-02-05 04:16:27</td>
        </tr>
        <tr>
            <td>2013-02-05 04:16:36</td>
        </tr>
        <tr>
            <td>2013-02-05 04:16:55</td>
        </tr>
        <tr>
            <td>2013-02-05 04:17:02</td>
        </tr>
        <tr>
            <td>2013-02-05 04:17:20</td>
        </tr>
        <tr>
            <td>2013-02-05 04:17:27</td>
        </tr>
        <tr>
            <td>2013-02-05 04:17:43</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:06</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:15</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:21</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:31</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:44</td>
        </tr>
        <tr>
            <td>2013-02-05 04:18:50</td>
        </tr>
        <tr>
            <td>2013-02-05 04:19:11</td>
        </tr>
        <tr>
            <td>2013-02-05 04:19:20</td>
        </tr>
        <tr>
            <td>2013-02-05 04:19:26</td>
        </tr>
        <tr>
            <td>2013-02-05 04:19:32</td>
        </tr>
        <tr>
            <td>2013-02-05 04:19:53</td>
        </tr>
        <tr>
            <td>2013-02-05 04:20:02</td>
        </tr>
        <tr>
            <td>2013-02-05 04:20:24</td>
        </tr>
        <tr>
            <td>2013-02-05 15:35:28</td>
        </tr>
        <tr>
            <td>2013-02-05 15:35:38</td>
        </tr>
        <tr>
            <td>2013-02-05 15:35:47</td>
        </tr>
        <tr>
            <td>2013-02-05 15:35:54</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:01</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:10</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:24</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:33</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:37</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:42</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:48</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:54</td>
        </tr>
        <tr>
            <td>2013-02-05 15:36:59</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:08</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:13</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:20</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:27</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:33</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:37</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:42</td>
        </tr>
        <tr>
            <td>2013-02-05 15:37:45</td>
        </tr>
    </table>



2. Use DISTINCT to remove duplicate rows
----------------------------------------

Especially in databases like the Dognition database where no primary
keys were declared in each table, sometimes entire duplicate rows can be
entered in error. Even with no duplicate rows present, sometimes your
queries correctly output multiple instances of the same value in a
column, but you are interested in knowing what the different possible
values in the column are, not what each value in each row is. In both of
these cases, the best way to arrive at the clean results you want is to
instruct the query to return only values that are distinct, or different
from all the rest. The SQL keyword that allows you to do this is called
DISTINCT. To use it in a query, place it directly after the word SELECT
in your query.

For example, if we wanted a list of all the breeds of dogs in the
Dognition database, we could try the following query from a previous
exercise:

.. code:: mysql

    SELECT breed
    FROM dogs;

However, the output of this query would not be very helpful, because it
would output the entry for every single row in the breed column of the
dogs table, regardless of whether it duplicated the breed of a previous
entry. Fortunately, we could arrive at the list we want by executing the
following query with the DISTINCT modifier:

.. code:: mysql

    SELECT DISTINCT breed
    FROM dogs;

**Try it yourself (If you do not limit your output, you should get 2006
rows in your output):**

.. code:: ipython3

    %%sql
    SELECT DISTINCT breed 
    FROM dogs;


.. parsed-literal::

    2006 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>breed</th>
        </tr>
        <tr>
            <td>Labrador Retriever</td>
        </tr>
        <tr>
            <td>Shetland Sheepdog</td>
        </tr>
        <tr>
            <td>Golden Retriever</td>
        </tr>
        <tr>
            <td>Shih Tzu</td>
        </tr>
        <tr>
            <td>Siberian Husky</td>
        </tr>
        <tr>
            <td>Mixed</td>
        </tr>
        <tr>
            <td>Shih Tzu-Poodle Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Vizsla</td>
        </tr>
        <tr>
            <td>Pug</td>
        </tr>
        <tr>
            <td>Boxer</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Nova Scotia Duck Tolling Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever</td>
        </tr>
        <tr>
            <td>Border Collie</td>
        </tr>
        <tr>
            <td>Belgian Malinois</td>
        </tr>
        <tr>
            <td>Australian Shepherd-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Poodle</td>
        </tr>
        <tr>
            <td>Golden Doodle</td>
        </tr>
        <tr>
            <td>German Shepherd Dog</td>
        </tr>
        <tr>
            <td>Weimaraner</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres</td>
        </tr>
        <tr>
            <td>Mudi</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Dalmatian</td>
        </tr>
        <tr>
            <td>I Don&#x27;t Know</td>
        </tr>
        <tr>
            <td>Border Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren</td>
        </tr>
        <tr>
            <td>Australian Terrier</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog</td>
        </tr>
        <tr>
            <td>Chihuahua- Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Finnish Spitz</td>
        </tr>
        <tr>
            <td>Rottweiler</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi</td>
        </tr>
        <tr>
            <td>Brussels Griffon</td>
        </tr>
        <tr>
            <td>French Bulldog</td>
        </tr>
        <tr>
            <td>Doberman Pinscher</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier</td>
        </tr>
        <tr>
            <td>Russell Terrier</td>
        </tr>
        <tr>
            <td>Irish Setter</td>
        </tr>
        <tr>
            <td>Irish Red and White Setter</td>
        </tr>
        <tr>
            <td>Poodle-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier</td>
        </tr>
        <tr>
            <td>Beagle-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Greyhound</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Labradoodle</td>
        </tr>
        <tr>
            <td>Cocker Spaniel</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Lhasa Apso-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel</td>
        </tr>
        <tr>
            <td>Neapolitan Mastiff</td>
        </tr>
        <tr>
            <td>Rat Terrier</td>
        </tr>
        <tr>
            <td>Border Terrier</td>
        </tr>
        <tr>
            <td>Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Dachshund</td>
        </tr>
        <tr>
            <td>Golden Retriever-Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Papillon Mix</td>
        </tr>
        <tr>
            <td>Papillon</td>
        </tr>
        <tr>
            <td>Pomeranian</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Maltese-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd</td>
        </tr>
        <tr>
            <td>Shiba Inu</td>
        </tr>
        <tr>
            <td>Border Collie-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Maltese-Poodle Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chihuahua</td>
        </tr>
        <tr>
            <td>Golden Retriever-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback</td>
        </tr>
        <tr>
            <td>West Highland White Terrier</td>
        </tr>
        <tr>
            <td>Poodle-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Silky Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog- Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Kooikerhondje</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier</td>
        </tr>
        <tr>
            <td>Bulldog</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Canaan Dog- Mix</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer</td>
        </tr>
        <tr>
            <td>Russell Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Border Collie Mix</td>
        </tr>
        <tr>
            <td>French Spaniel</td>
        </tr>
        <tr>
            <td>Italian Greyhound</td>
        </tr>
        <tr>
            <td>Leonberger</td>
        </tr>
        <tr>
            <td>Portuguese Water Dog</td>
        </tr>
        <tr>
            <td>Boykin Spaniel</td>
        </tr>
        <tr>
            <td>Soft Coated Wheaten Terrier</td>
        </tr>
        <tr>
            <td>Boston Terrier</td>
        </tr>
        <tr>
            <td>Brittany</td>
        </tr>
        <tr>
            <td>Golden Retriever-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Nova Scotia Duck Tolling Retriever</td>
        </tr>
        <tr>
            <td>Lhasa Apso</td>
        </tr>
        <tr>
            <td>American Eskimo Dog</td>
        </tr>
        <tr>
            <td>Keeshond</td>
        </tr>
        <tr>
            <td>Bull Terrier</td>
        </tr>
        <tr>
            <td>Shih Tzu-Maltese Mix</td>
        </tr>
        <tr>
            <td>Maltese</td>
        </tr>
        <tr>
            <td>Cockapoo</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Maltese-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Miniature American Shepherd</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher</td>
        </tr>
        <tr>
            <td>English Setter</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer-Poodle Mix</td>
        </tr>
        <tr>
            <td>Havanese</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Cane Corso Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Pointer-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Basenji Mix</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Poodle-Maltese Mix</td>
        </tr>
        <tr>
            <td>Great Dane-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Poodle Mix</td>
        </tr>
        <tr>
            <td>Scottish Terrier</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Tibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Great Dane</td>
        </tr>
        <tr>
            <td>Icelandic Sheepdog</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Pug-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier- Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog- Mix</td>
        </tr>
        <tr>
            <td>Old English Sheepdog</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Boxer Mix</td>
        </tr>
        <tr>
            <td>Poodle-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Other</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Terrier- Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear</td>
        </tr>
        <tr>
            <td>American Water Spaniel</td>
        </tr>
        <tr>
            <td>Russell Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Mastiff</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Dachshund Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Rottweiler- Mix</td>
        </tr>
        <tr>
            <td>Pug-Maltese Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Whippet</td>
        </tr>
        <tr>
            <td>Boston Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Welsh Springer Spaniel</td>
        </tr>
        <tr>
            <td>Poodle-Old English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier</td>
        </tr>
        <tr>
            <td>Border Collie-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Poodle Mix</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Collie Mix</td>
        </tr>
        <tr>
            <td>Collie</td>
        </tr>
        <tr>
            <td>Golden Retriever-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Norfolk Terrier</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Wire Fox Terrier</td>
        </tr>
        <tr>
            <td>Samoyed</td>
        </tr>
        <tr>
            <td>Labrador Retriever-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Puggle</td>
        </tr>
        <tr>
            <td>Beagle- Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Poodle-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Pug-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Pug-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Poodle-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Polish Lowland Sheepdog</td>
        </tr>
        <tr>
            <td>Miniature Pinscher</td>
        </tr>
        <tr>
            <td>Chinese Crested-Poodle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Poodle-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Boxer-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Great Dane-Irish Wolfhound Mix</td>
        </tr>
        <tr>
            <td>Pyrenean Shepherd</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Boxer Mix</td>
        </tr>
        <tr>
            <td>Akita</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Beagle-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Beagle Mix</td>
        </tr>
        <tr>
            <td>Silky Terrier</td>
        </tr>
        <tr>
            <td>-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever- Mix</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Shorkie</td>
        </tr>
        <tr>
            <td>Field Spaniel</td>
        </tr>
        <tr>
            <td>Chihuahua-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Newfoundland</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound</td>
        </tr>
        <tr>
            <td>Pug-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Whippet-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Vizsla- Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Whippet Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basenji</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Giant Schnauzer</td>
        </tr>
        <tr>
            <td>Bugg</td>
        </tr>
        <tr>
            <td>Poodle-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Poodle-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>BullBoxer</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise</td>
        </tr>
        <tr>
            <td>Poodle- Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Lagotto Romagnolo</td>
        </tr>
        <tr>
            <td>Rat Terrier-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested</td>
        </tr>
        <tr>
            <td>Irish Wolfhound</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier</td>
        </tr>
        <tr>
            <td>Standard Schnauzer</td>
        </tr>
        <tr>
            <td>Greater Swiss Mountain Dog</td>
        </tr>
        <tr>
            <td>Plott-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Bulldog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Plott Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Mastiff-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Norfolk Terrier Mix</td>
        </tr>
        <tr>
            <td>Great Pyrenees</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Belgian Malinois Mix</td>
        </tr>
        <tr>
            <td>Redbone Coonhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Poodle Mix</td>
        </tr>
        <tr>
            <td>Tibetan Spaniel</td>
        </tr>
        <tr>
            <td>Treeing Walker Coonhound</td>
        </tr>
        <tr>
            <td>English Springer Spaniel- Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier</td>
        </tr>
        <tr>
            <td>Spinone Italiano</td>
        </tr>
        <tr>
            <td>Bulldog-Pug Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Poodle-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Miniature Bull Terrier</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Pug Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde</td>
        </tr>
        <tr>
            <td>Redbone Coonhound</td>
        </tr>
        <tr>
            <td>Maltese-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>Basenji-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Skye Terrier</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Wirehaired Pointing Griffon</td>
        </tr>
        <tr>
            <td>Chinese Crested-Pug Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd</td>
        </tr>
        <tr>
            <td>Norwich Terrier</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Maltese Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Kerry Blue Terrier</td>
        </tr>
        <tr>
            <td>Chinook</td>
        </tr>
        <tr>
            <td>Berger Picard</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Pointer Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie</td>
        </tr>
        <tr>
            <td>Alaskan Malamute</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Portuguese Podengo Mix</td>
        </tr>
        <tr>
            <td>Black Russian Terrier</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog</td>
        </tr>
        <tr>
            <td>Tibetan Terrier</td>
        </tr>
        <tr>
            <td>Chow Chow-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Welsh Terrier</td>
        </tr>
        <tr>
            <td>Norwegian Elkhound</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>St. Bernard</td>
        </tr>
        <tr>
            <td>Boxer-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Mudi-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Pekingese</td>
        </tr>
        <tr>
            <td>Australian Shepherd- Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog</td>
        </tr>
        <tr>
            <td>Eurasier</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Poodle Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier- Mix</td>
        </tr>
        <tr>
            <td>Pointer-Beagle Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>-Collie Mix</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Redbone Coonhound-Vizsla Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>St. Bernard-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound</td>
        </tr>
        <tr>
            <td>Chow Chow-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Ibizan Hound</td>
        </tr>
        <tr>
            <td>Golden Retriever-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pug Mix</td>
        </tr>
        <tr>
            <td>Border Collie- Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Labradoodle</td>
        </tr>
        <tr>
            <td>Shiba Inu-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever- Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Pomapoo</td>
        </tr>
        <tr>
            <td>Lakeland Terrier</td>
        </tr>
        <tr>
            <td>Papillon-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>Basset Hound</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Briard</td>
        </tr>
        <tr>
            <td>Irish Terrier</td>
        </tr>
        <tr>
            <td>Puli</td>
        </tr>
        <tr>
            <td>Greyhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Poodle-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Redbone Coonhound-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Deutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>Norwegian Buhund</td>
        </tr>
        <tr>
            <td>Italian Greyhound-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dogo Argentino</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Swedish Vallhund</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Miniature Pinscher-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Pomeranian-Basenji Mix</td>
        </tr>
        <tr>
            <td>Portuguese Podengo Pequeno</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Glen of Imaal Terrier</td>
        </tr>
        <tr>
            <td>Boxer-Ibizan Hound Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Pug-Beagle Mix</td>
        </tr>
        <tr>
            <td>Japanese Chin</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Boxer-Vizsla Mix</td>
        </tr>
        <tr>
            <td>Redbone Coonhound-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Plott Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Curly-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Maltese-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Toy Fox Terrier</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>American Foxhound- Mix</td>
        </tr>
        <tr>
            <td>German Spitz</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Poodle-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Italian Greyhound-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Great Pyrenees-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier- Mix</td>
        </tr>
        <tr>
            <td>Shetland Sheepdog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Maltese-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Otterhound</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier- Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Papillon-Poodle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Boxer Mix</td>
        </tr>
        <tr>
            <td>St. Bernard- Mix</td>
        </tr>
        <tr>
            <td>Boxer-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier- Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Saluki Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Akita Mix</td>
        </tr>
        <tr>
            <td>Poodle-Welsh Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>Nova Scotia Duck Tolling Retriever- Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Keeshond-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer</td>
        </tr>
        <tr>
            <td>Great Dane-Pointer Mix</td>
        </tr>
        <tr>
            <td>Samoyed-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>English Setter-Beagle Mix</td>
        </tr>
        <tr>
            <td>Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Akita- Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Whippet-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Schapendoes</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>Poodle-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Beagle-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Kai Ken</td>
        </tr>
        <tr>
            <td>Irish Terrier-Gordon Setter Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Basenji Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Poodle Mix</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer-Scottish Terrier Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog- Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Entlebucher Mountain Dog</td>
        </tr>
        <tr>
            <td>Spanish Water Dog</td>
        </tr>
        <tr>
            <td>Lowchen</td>
        </tr>
        <tr>
            <td>Curly-Coated Retriever</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Smooth Fox Terrier</td>
        </tr>
        <tr>
            <td>Pharaoh Hound</td>
        </tr>
        <tr>
            <td>Clumber Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Whippet-Poodle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Miniature Pinscher-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Newfoundland-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Portuguese Podengo</td>
        </tr>
        <tr>
            <td>-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Borzoi</td>
        </tr>
        <tr>
            <td>-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>German Pinscher</td>
        </tr>
        <tr>
            <td>Labrador Retriever-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Finnish Lapphund</td>
        </tr>
        <tr>
            <td>Czechoslovakian Vlcak</td>
        </tr>
        <tr>
            <td>-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pointer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Portuguese Pointer</td>
        </tr>
        <tr>
            <td>Golden Retriever-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer-Maltese Mix</td>
        </tr>
        <tr>
            <td>Whippet-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Whippet Mix</td>
        </tr>
        <tr>
            <td>Redbone Coonhound-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Canaan Dog</td>
        </tr>
        <tr>
            <td>Boxer- Mix</td>
        </tr>
        <tr>
            <td>German Wirehaired Pointer</td>
        </tr>
        <tr>
            <td>Cane Corso</td>
        </tr>
        <tr>
            <td>Keeshond-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Weimaraner-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Hairless Terrier</td>
        </tr>
        <tr>
            <td>Border Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Pug-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Havanese-Poodle Mix</td>
        </tr>
        <tr>
            <td>Pomeranian-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Whippet-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Pointer Mix</td>
        </tr>
        <tr>
            <td>Boxer-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Poodle-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Miniature Pinscher- Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Pug Mix</td>
        </tr>
        <tr>
            <td>American Foxhound</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Scottish Deerhound</td>
        </tr>
        <tr>
            <td>Saluki</td>
        </tr>
        <tr>
            <td>-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer- Mix</td>
        </tr>
        <tr>
            <td>-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Havanese-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pug Mix</td>
        </tr>
        <tr>
            <td>Grand Basset Griffon Vendeen</td>
        </tr>
        <tr>
            <td>Old English Sheepdog-Poodle Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Schipperke</td>
        </tr>
        <tr>
            <td>Jindo-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Collie- Mix</td>
        </tr>
        <tr>
            <td>-Beagle Mix</td>
        </tr>
        <tr>
            <td>Basenji- Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>-Boxer Mix</td>
        </tr>
        <tr>
            <td>-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Hovawart</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Basset Hound- Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>-Poodle Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Poodle-German Spitz Mix</td>
        </tr>
        <tr>
            <td>West Highland White Terrier-Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Lhasa Apso-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bulldog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier- Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Akita Mix</td>
        </tr>
        <tr>
            <td>-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Mastiff-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Pug-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu- Mix</td>
        </tr>
        <tr>
            <td>Treeing Walker Coonhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Newfoundland-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Weimaraner- Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky- Mix</td>
        </tr>
        <tr>
            <td>-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Treeing Walker Coonhound- Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Silky Terrier-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Russian Toy</td>
        </tr>
        <tr>
            <td>Chihuahua-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Beagle Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Poodle-Tibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Whippet-Tibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever- Mix</td>
        </tr>
        <tr>
            <td>Perro de Presa Canario</td>
        </tr>
        <tr>
            <td>Irish Water Spaniel</td>
        </tr>
        <tr>
            <td>West Highland White Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Pumi</td>
        </tr>
        <tr>
            <td>Clumber Spaniel</td>
        </tr>
        <tr>
            <td>Poodle-Papillon Mix</td>
        </tr>
        <tr>
            <td>Old English Sheepdog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Jack-A-Poo</td>
        </tr>
        <tr>
            <td>Pointer</td>
        </tr>
        <tr>
            <td>Mastiff-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Wirehaired Vizsla</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow</td>
        </tr>
        <tr>
            <td>Chihuahua-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Akita-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog- Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Manchester Terrier</td>
        </tr>
        <tr>
            <td>Golden Retriever-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Pug-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Miniature Pinscher-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier- Mix</td>
        </tr>
        <tr>
            <td>-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Japanese Chin-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pug Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Scottish Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Bulldog-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Pointer Mix</td>
        </tr>
        <tr>
            <td>Poodle-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Beauceron</td>
        </tr>
        <tr>
            <td>Border Collie-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>St. Bernard-Brittany Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>-Whippet Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Maltese-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Basenji Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Dachshund- Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Pointer Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Maltese Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Poodle-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Perro de Presa Canario-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Maltese- Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Lhasa Apso- Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Basenji-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Lagotto Romagnolo-Schapendoes Mix</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer- Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Bolognese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Papillon Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Poodle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Havanese-Maltese Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Boxer Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound- Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>-Pug Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Pug-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Ibizan Hound Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Maltese-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Keeshond-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Gordon Setter</td>
        </tr>
        <tr>
            <td>Beagle-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Lhasa Apso-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute- Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Akita-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Irish Terrier Mix</td>
        </tr>
        <tr>
            <td>-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Pembroke Welsh Corgi-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Icelandic Sheepdog-Keeshond Mix</td>
        </tr>
        <tr>
            <td>English Foxhound</td>
        </tr>
        <tr>
            <td>Beagle-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Bloodhound</td>
        </tr>
        <tr>
            <td>Pomeranian-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Pomeranian-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>English Setter-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Brittany Mix</td>
        </tr>
        <tr>
            <td>Shih Tzu-Silky Terrier Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Pointer-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois- Mix</td>
        </tr>
        <tr>
            <td>Karelian Bear Dog</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Irish Wolfhound-Great Dane Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog- Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Basenji-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>-Otterhound Mix</td>
        </tr>
        <tr>
            <td>Miniature Schnauzer-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Central Asian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Whippet Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Irish Setter-Poodle Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel- Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Boxer Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Treeing Walker Coonhound-English Foxhound Mix</td>
        </tr>
        <tr>
            <td>-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Miniature Pinscher-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Komondor</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Akita Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Small Munsterlander Pointer</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer-Pointer Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Pug Mix</td>
        </tr>
        <tr>
            <td>-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Collie Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei- Mix</td>
        </tr>
        <tr>
            <td>Standard Schnauzer-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boxer-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Maltese-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Rottweiler-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Brittany-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Beagle Mix</td>
        </tr>
        <tr>
            <td>Manchester Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Poodle-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Neapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Pug-Brussels Griffon Mix</td>
        </tr>
        <tr>
            <td>Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Papillon-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Stabyhoun Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Scottish Deerhound-Saluki Mix</td>
        </tr>
        <tr>
            <td>Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-Border Collie Mix</td>
        </tr>
        <tr>
            <td>-Polish Lowland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Greyhound-Bedlington Terrier Mix</td>
        </tr>
        <tr>
            <td>Pomeranian-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Nova Scotia Duck Tolling Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Beaglier</td>
        </tr>
        <tr>
            <td>Rat Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff- Mix</td>
        </tr>
        <tr>
            <td>Pointer-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Siberian Husky-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise- Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Whippet Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Smooth Fox Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Greyhound-Saluki Mix</td>
        </tr>
        <tr>
            <td>Brittany-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>St. Bernard-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Tosa- Mix</td>
        </tr>
        <tr>
            <td>Newfoundland-Bergamasco Mix</td>
        </tr>
        <tr>
            <td>Border Collie-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Collie Mix</td>
        </tr>
        <tr>
            <td>Greyhound-Scottish Deerhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Grand Basset Griffon Vendeen- Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Cirneco dell&quot;Etna</td>
        </tr>
        <tr>
            <td>Dachshund-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Parson Russell Terrier-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Norfolk Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Field Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Lakeland Terrier Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Greyhound-Whippet Mix</td>
        </tr>
        <tr>
            <td>Petit Basset Griffon Vendeen</td>
        </tr>
        <tr>
            <td>-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Thai Ridgeback</td>
        </tr>
        <tr>
            <td>Basset Hound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Whippet-Saluki Mix</td>
        </tr>
        <tr>
            <td>Great Dane-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>German Shorthaired Pointer-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Maltese-Tibetan Spaniel Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Poodle-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Staffordshire Bull Terrier-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>West Highland White Terrier-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Xoloitzcuintli</td>
        </tr>
        <tr>
            <td>Maltese-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Greyhound-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Maltese Mix</td>
        </tr>
        <tr>
            <td>Maltese-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde- Mix</td>
        </tr>
        <tr>
            <td>Stabyhoun</td>
        </tr>
        <tr>
            <td>Irish Setter-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Collie Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Appenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>-Maltese Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boerboel</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Boerboel Mix</td>
        </tr>
        <tr>
            <td>Havanese-Chinese Crested Mix</td>
        </tr>
        <tr>
            <td>Tibetan Mastiff</td>
        </tr>
        <tr>
            <td>Braque du Bourbonnais</td>
        </tr>
        <tr>
            <td>Havanese-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Scottish Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Pug- Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Mastiff-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Rhodesian Ridgeback-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Field Spaniel Mix</td>
        </tr>
        <tr>
            <td>Gordon Setter- Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Irish Red and White Setter Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Russell Terrier-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Papillon Mix</td>
        </tr>
        <tr>
            <td>Norwich Terrier- Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bergamasco-Old English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Maltese-Silky Terrier Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>German Spitz-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>West Highland White Terrier-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund- Mix</td>
        </tr>
        <tr>
            <td>Tibetan Spaniel-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Labrador Retriever-Vizsla Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Pekingese-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Rat Terrier-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Pug-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Shetland Sheepdog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>English Setter- Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Japanese Chin-Papillon Mix</td>
        </tr>
        <tr>
            <td>Great Pyrenees-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>English Foxhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Mastiff-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Drentsche Patrijshond</td>
        </tr>
        <tr>
            <td>Yorkshire Terrier-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Peruvian Inca Orchid</td>
        </tr>
        <tr>
            <td>Beagle-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Irish Setter-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Golden Retriever-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Pomeranian-Papillon Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Sloughi-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Greater Swiss Mountain Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Plott Mix</td>
        </tr>
        <tr>
            <td>Plott</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Brittany Mix</td>
        </tr>
        <tr>
            <td>St. Bernard-Greater Swiss Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Great Dane-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Cocker Spaniel Mix</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">2006 rows, truncated to displaylimit of 1000</span>



If you scroll through the output, you will see that no two entries are
the same. Of note, if you use the DISTINCT clause on a column that has
NULL values, MySQL will include one NULL value in the DISTINCT output
from that column.

 When the DISTINCT clause is used with multiple columns in a SELECT
statement, the combination of all the columns together is used to
determine the uniqueness of a row in a result set.

For example, if you wanted to know all the possible combinations of
states and cities in the users table, you could query:

.. code:: mysql

    SELECT DISTINCT state, city
    FROM users;

**Try it (if you don't limit your output you'll see 3999 rows in the
query result, of which the first 1000 are displayed):**

.. code:: ipython3

    %%sql
    SELECT DISTINCT state, city
    FROM users;


.. parsed-literal::

    3999 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>state</th>
            <th>city</th>
        </tr>
        <tr>
            <td>ND</td>
            <td>Grand Forks</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Barre</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Darien</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Winnetka</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Raleigh</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Auburn</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Fort Collins</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Seattle</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Bainbridge Island</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Bremerton</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Aptos</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>North Ridgeville</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Charlottesville</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Hillsborough</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>New York</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Los Angeles</td>
        </tr>
        <tr>
            <td>WY</td>
            <td>Worland</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Grayslake</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Falls Church</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Everett</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Dixon</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Altadena</td>
        </tr>
        <tr>
            <td>A</td>
            <td>Rosenau</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Sierra Vista</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Durham</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Northbrook</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Cincinnati</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Charlotte</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Boston</td>
        </tr>
        <tr>
            <td>AE</td>
            <td>Boston</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Birdsboro</td>
        </tr>
        <tr>
            <td>83</td>
            <td>Rødekro</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Alexandria</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Charlotte</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Woodinville</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Woodinville</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Oakland</td>
        </tr>
        <tr>
            <td>1</td>
            <td>Singapore</td>
        </tr>
        <tr>
            <td>DC</td>
            <td>Oakland</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Oakland</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Test</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Test</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Oreland</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Carrboro</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Carrboro</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Cary</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Carrboro</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Melbourne</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Alexandria</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Alexandria</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Singapore</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Mountain View</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Mountain View</td>
        </tr>
        <tr>
            <td>MO</td>
            <td>Bloomfield Hills</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Owings</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Bloomfield Hills</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Philadelphia</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Durham</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Test</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Test</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Davis</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Davis</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Davis</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Goshen</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Spokane</td>
        </tr>
        <tr>
            <td>MO</td>
            <td>Saint Louis</td>
        </tr>
        <tr>
            <td>DC</td>
            <td>Washington</td>
        </tr>
        <tr>
            <td>LA</td>
            <td>Denham Springs</td>
        </tr>
        <tr>
            <td>NV</td>
            <td>Henderson</td>
        </tr>
        <tr>
            <td>LND</td>
            <td>London </td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Hancock</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Old Lyme</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Duncanville</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Victoria</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Portland</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Southington</td>
        </tr>
        <tr>
            <td>HI</td>
            <td>Kapolei</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Suffield</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Atlanta</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Fort Lauderdale</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Spring</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Virginia Beach</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Minneapolis</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Jonesboro</td>
        </tr>
        <tr>
            <td>AE</td>
            <td>Apo</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Jersey City</td>
        </tr>
        <tr>
            <td>JM</td>
            <td>Lapid</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Clinton</td>
        </tr>
        <tr>
            <td>ZH</td>
            <td>Zurich</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Goodlettsville</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Princeton</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Oakland</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Nathrop</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Orlando</td>
        </tr>
        <tr>
            <td>F</td>
            <td>St. Privé St. Mesmin</td>
        </tr>
        <tr>
            <td>QLD</td>
            <td>Moorooka</td>
        </tr>
        <tr>
            <td>JU</td>
            <td>Delémont</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Mcminnville</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>Altoona</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Olathe</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Austin</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Philadelphia</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Jacksonville</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Cobble Hill</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>North Adams</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Sellersville</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>New Carlisle</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Alma</td>
        </tr>
        <tr>
            <td>N</td>
            <td>Rotorua</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Pennington</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Santa Fe</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Towson</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Carmel Valley</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Alpharetta</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Chemainus</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Macon</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Vancouver</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Bala Cynwyd</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Woodinville</td>
        </tr>
        <tr>
            <td>N</td>
            <td>Auckland</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Dallas</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Prairie Village</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Phoenix</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>San Marcos</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Cibolo</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Melbourne</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Santee</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Waterloo</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Kalamazoo</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Jamison</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Yorba Linda</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Chicago</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Chapel Hill</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Rixeyville</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Youngsville</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Toronto</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Bluffton</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Brookeville</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Houston</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Tijeras</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Memphis</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Golden</td>
        </tr>
        <tr>
            <td>N</td>
            <td>New Plymouth</td>
        </tr>
        <tr>
            <td>N/A</td>
            <td>Kennedy Town</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Marshall</td>
        </tr>
        <tr>
            <td>MO</td>
            <td>Columbia</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Somerville</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Boston</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Asheville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Port Washington</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Gastonia</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Irvine</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Ellensburg</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Cedar Crest</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Deerfield</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Freeland</td>
        </tr>
        <tr>
            <td>NV</td>
            <td>Las Vegas</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Phoenix</td>
        </tr>
        <tr>
            <td>OK</td>
            <td>Lindsay</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Tyrone</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Palo Alto</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Hereford</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Larkspur</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Arlington</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Vinton</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Quincy</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Dalton</td>
        </tr>
        <tr>
            <td>AB</td>
            <td>Calgary</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Ossineke</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Brooklyn</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Winston Salem</td>
        </tr>
        <tr>
            <td>AL</td>
            <td>Slocomb</td>
        </tr>
        <tr>
            <td>LA</td>
            <td>New Orleans</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Schaumburg</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>College Park</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Alexandria</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Woburn</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>West Linn</td>
        </tr>
        <tr>
            <td>84</td>
            <td>Frederiksberg</td>
        </tr>
        <tr>
            <td>RI</td>
            <td>Warwick</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Chesapeake Beach</td>
        </tr>
        <tr>
            <td>UT</td>
            <td>West Jordan</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Laredo</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Sarasota</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Hudson</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Missouri City</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>St. Davids</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Cottonwood</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Montrose</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Stroudsburg</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Saint Johns</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Berkeley</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Bonita Springs</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Albuquerque</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Bethesda</td>
        </tr>
        <tr>
            <td>AP</td>
            <td>Fpo</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Mukwonago</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Cambridge</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Rockville</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Thornhill</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Concord</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Columbus</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Keller</td>
        </tr>
        <tr>
            <td>AB</td>
            <td>Cardston</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Greensboro</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Douglasville</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Lynnwood</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Mosman</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Saint Petersburg</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>North Sydney</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Newfoundland</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Cranford</td>
        </tr>
        <tr>
            <td>QLD</td>
            <td>Hawthorne</td>
        </tr>
        <tr>
            <td>WLN</td>
            <td>Kirknewton</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Eildon</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Apex</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Ladera Ranch</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Mount Carmel</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Fort Myers</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Francisco</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Newton Highlands</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Pittsboro</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Ringwood</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Long Beach</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Wickliffe</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Zebulon</td>
        </tr>
        <tr>
            <td>83</td>
            <td>Odense Sv</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Richboro</td>
        </tr>
        <tr>
            <td>B</td>
            <td>Thessaloniki</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Rockport</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Indianapolis</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Greer</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Arlington</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Myrtle Beach</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Red Lion</td>
        </tr>
        <tr>
            <td>L</td>
            <td>Newbridge</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Nepean East</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>West Olive</td>
        </tr>
        <tr>
            <td>NLE</td>
            <td>Monterrey</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Driftwood</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Mertztown</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Tallahassee</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Glendale</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Concord</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Monroe</td>
        </tr>
        <tr>
            <td>37</td>
            <td>Tallinn</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Rochester</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Miami</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Stanwood</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Stratham</td>
        </tr>
        <tr>
            <td>OK</td>
            <td>Tulsa</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Ocean Grove</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Newbury</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Isanti</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Pittsburgh</td>
        </tr>
        <tr>
            <td>NW</td>
            <td>Essen</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Beaufort</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Sanford</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Mission</td>
        </tr>
        <tr>
            <td>ID</td>
            <td>Idaho Falls</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Swarthmore</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>New Albin</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Pasadena</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Brookline</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Charleston</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Diego</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Bedford</td>
        </tr>
        <tr>
            <td>84</td>
            <td>Charlottenlund</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Cromwell</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Eugene</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Burlingame</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Winchester</td>
        </tr>
        <tr>
            <td>84</td>
            <td>Copenhagen</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Germantown</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Newton Lower Falls</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Columbia</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Dublin</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Ottawa</td>
        </tr>
        <tr>
            <td>KY</td>
            <td>Ft Mitchell</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Herndon</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Englewood</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>La Jolla</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Roseville</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Kensington</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Oakland</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Manhasset</td>
        </tr>
        <tr>
            <td>TAS</td>
            <td>Somerset</td>
        </tr>
        <tr>
            <td>EDH</td>
            <td>Edinburgh</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Tinley Park</td>
        </tr>
        <tr>
            <td>AB</td>
            <td>Edmonton</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Beverly Hills</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Skokie</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Guatay</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Kanata</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Mc Lean</td>
        </tr>
        <tr>
            <td>KEN</td>
            <td>Tunbridge Wells</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Cuyahoga Falls</td>
        </tr>
        <tr>
            <td>MB</td>
            <td>Gladstone</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Tucson</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Belmont</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>New Hill</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Peachtree City</td>
        </tr>
        <tr>
            <td>QC</td>
            <td>Saint-eustache</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Camarillo</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Hyattsville</td>
        </tr>
        <tr>
            <td>NE</td>
            <td>Papillion</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Jose</td>
        </tr>
        <tr>
            <td>AL</td>
            <td>Mobile</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Westborough</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Acworth</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Marietta</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Midland</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Clayton</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Baltimore</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Somerset</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Mount Pleasant</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Grand Rapids</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Beverly</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Aas</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Lake George</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Mill Valley</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Pound Ridge</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Manhattan Beach</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Kirkland</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Valencia</td>
        </tr>
        <tr>
            <td>1</td>
            <td>Nordre Frogn</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Southern Pines</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Lancaster</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Granite Falls</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Ansonia</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Charlestown</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Madison</td>
        </tr>
        <tr>
            <td>AR</td>
            <td>De Witt</td>
        </tr>
        <tr>
            <td>BB</td>
            <td>Berlin</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Richmond</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Conshohocken</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Flower Mound</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Waynesville</td>
        </tr>
        <tr>
            <td>GBN</td>
            <td>Devizes</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Westminster</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Puchberg/schneeberg</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Saint Paul</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Parker</td>
        </tr>
        <tr>
            <td>UKM</td>
            <td>Brighton</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Milford</td>
        </tr>
        <tr>
            <td>KEN</td>
            <td>Ramsgate </td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Palos Verdes Peninsula</td>
        </tr>
        <tr>
            <td>QLD</td>
            <td>Mackay</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Naples</td>
        </tr>
        <tr>
            <td>78</td>
            <td>Tartu</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Holly Springs</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Reading</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Brookfield</td>
        </tr>
        <tr>
            <td>N/A</td>
            <td>Test</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Ann Arbor</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Hawleyville</td>
        </tr>
        <tr>
            <td>LA</td>
            <td>Shreveport</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Salinas</td>
        </tr>
        <tr>
            <td>RJ</td>
            <td>Niterói</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Pensacola</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Sammamish</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Santa Rosa</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Williston</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Gaithersburg</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Riverhead</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Ronkonkoma</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Ottawa</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Lancaster</td>
        </tr>
        <tr>
            <td>PR</td>
            <td>Yabucoa</td>
        </tr>
        <tr>
            <td>UT</td>
            <td>Salt Lake City</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Astoria</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Schenectady</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Eastlake</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Delaware</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Crestone</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Ojai</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Woodstock</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Black Earth</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Bloomington</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Plano</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Tacoma</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Pinehurst</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Fleming Island</td>
        </tr>
        <tr>
            <td>NV</td>
            <td>Minden</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Arlington</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Locust Valley</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Centreville</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Ventura</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Menlo Park</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Clarksburg</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Lake Oswego</td>
        </tr>
        <tr>
            <td>AB</td>
            <td>Cochrane</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Needham</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Aurora</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Melbourne</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Four Oaks</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Westford</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Sault Sainte Marie</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Auburndale</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>South Pasadena</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Medford</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>San Tan Valley</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Saddle Brook</td>
        </tr>
        <tr>
            <td>CAM</td>
            <td>Huntingdon</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>North Hollywood</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Renton</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Medford</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Wakefield</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Hobe Sound</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Fort Mill</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Alameda</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Lawrenceville</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Reedley</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Lovettsville</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Efland</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Redwood City</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Cranbourne North</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Bakersfield</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Sloatsburg</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>King George</td>
        </tr>
        <tr>
            <td>C</td>
            <td>Galway</td>
        </tr>
        <tr>
            <td>SOM</td>
            <td>Bath</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Sylvania</td>
        </tr>
        <tr>
            <td>KY</td>
            <td>Louisville</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Roslindale</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Springfield</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Bellingham</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Vermontville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Bronx</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Singapore</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Belmont</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Solvang</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Pueblo</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Concord</td>
        </tr>
        <tr>
            <td>NV</td>
            <td>Sparks</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Vancouver</td>
        </tr>
        <tr>
            <td>R</td>
            <td>Saint Jean De Monts</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Montpelier</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>West Newton</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Citrus Heights</td>
        </tr>
        <tr>
            <td>VL</td>
            <td>Vilnius</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Statesville</td>
        </tr>
        <tr>
            <td>UKM</td>
            <td>Chippenham</td>
        </tr>
        <tr>
            <td>QC</td>
            <td>Montreal</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Carlsbad</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Wilmington</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sherman Oaks</td>
        </tr>
        <tr>
            <td>LIN</td>
            <td>Grimsby</td>
        </tr>
        <tr>
            <td>HI</td>
            <td>Kailua</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Hampstead</td>
        </tr>
        <tr>
            <td>ME</td>
            <td>Orland</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Cincinnati</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Manchester Center</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Onalaska</td>
        </tr>
        <tr>
            <td>N/A</td>
            <td>Stapleford</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Clemente</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Littleton</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Ashwood</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Oshawa</td>
        </tr>
        <tr>
            <td>DIF</td>
            <td>Mexico City</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Beeton</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Swanzey</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Topeka</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Seguin</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Escondido</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Seaside</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Waynesville</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Reynoldsburg</td>
        </tr>
        <tr>
            <td>0</td>
            <td>Quezon City</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Moscow</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Craig</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Danielson</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Ferndale</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Newport News</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Woodbridge</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Ben Lomond</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Amherst</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Nyack</td>
        </tr>
        <tr>
            <td>RI</td>
            <td>Barrington</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>New Port Richey</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Dublin</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Carmel</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Chappaqua</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Dover</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Amherst</td>
        </tr>
        <tr>
            <td>N/A</td>
            <td>Singapore</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Portsmouth</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Scottsdale</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Brighton</td>
        </tr>
        <tr>
            <td>AK</td>
            <td>Anchorage</td>
        </tr>
        <tr>
            <td>HI</td>
            <td>Kapaa</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Coronado</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Mountain View</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Basalt</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Northampton</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Knoxville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Spencertown</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Morristown</td>
        </tr>
        <tr>
            <td>D</td>
            <td>Karkur</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Gary</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Holland</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Brentwood</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Aiken</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Steamboat Springs</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sacramento</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Quincy</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Trenton</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Boulder</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>New Canaan</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Mercer Island</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Daly City</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Westfield</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Scarsdale</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Williamsburg</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>York</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sunnyvale</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Dunedin</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Cape Coral</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Hingham</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Allston</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>New Paltz</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Pleasantville</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Manasquan</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Santa Monica</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Sequim</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Elkins Park</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Lansdowne</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Hainesport</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Rockledge</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Chevy Chase</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Larchmont</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Norwalk</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Van Nuys</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Woodbridge</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Erie</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Smyrna</td>
        </tr>
        <tr>
            <td>RI</td>
            <td>Westerly</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Jamaica</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Nashville</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Midlothian</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Dandridge</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Woodland</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Concord</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Chelsea</td>
        </tr>
        <tr>
            <td>BY</td>
            <td>Munich</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Rock Hill</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Toledo</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Spencer</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Montclair</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Potomac</td>
        </tr>
        <tr>
            <td>AK</td>
            <td>Fairbanks</td>
        </tr>
        <tr>
            <td>AR</td>
            <td>Little Rock</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sausalito</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Athens</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Tunkhannock</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Las Vegas</td>
        </tr>
        <tr>
            <td>88</td>
            <td>Cagliari</td>
        </tr>
        <tr>
            <td>RM</td>
            <td>Santiago</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Brighton</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Purcellville</td>
        </tr>
        <tr>
            <td>75</td>
            <td>Cassano Delle Murge</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Tampa</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>West Palm Beach</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Bend</td>
        </tr>
        <tr>
            <td>MT</td>
            <td>Bozeman</td>
        </tr>
        <tr>
            <td>GE</td>
            <td>Vandoeuvres </td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Cleveland</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Santa Cruz</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Princeton</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Stamford</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Paddington</td>
        </tr>
        <tr>
            <td>21</td>
            <td>Torino</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Saint Simons Island</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Mc Farland</td>
        </tr>
        <tr>
            <td>NW</td>
            <td>Duesseldorf</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Odessa</td>
        </tr>
        <tr>
            <td>MO</td>
            <td>Kansas City</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Stinson Beach</td>
        </tr>
        <tr>
            <td>83</td>
            <td>Tranekær</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Bloomfield Hills</td>
        </tr>
        <tr>
            <td>J</td>
            <td>Paris</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>East Northport</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Bonsall</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Boynton Beach</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Marshall</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Matthews</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Los Gatos</td>
        </tr>
        <tr>
            <td>NM</td>
            <td>Placitas</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Silver Spring</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Lansdale</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Greenlawn</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Morrisville</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Cape May</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Wimberley</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Easton</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Greenwich</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Sparks Glencoe</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Mound</td>
        </tr>
        <tr>
            <td>1</td>
            <td>Oslo</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Summit</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Benicia</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Ellicott City</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Manhattan</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Landrum</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Hillsboro</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Apple Valley</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Andover</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Ontario</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>New Albany</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Gibsonville</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Champaign</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Cass City</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Ypsilanti</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Columbia</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Winter Park</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Bristol</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Frederick</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Lebanon</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Gainesville</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Tempe</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Lower Salem</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Davidson</td>
        </tr>
        <tr>
            <td>ME</td>
            <td>New Gloucester</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Niagara University</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Ridgewood</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Norfolk</td>
        </tr>
        <tr>
            <td>OK</td>
            <td>Oklahoma City</td>
        </tr>
        <tr>
            <td>ME</td>
            <td>Orono</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Westport</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Fairfield</td>
        </tr>
        <tr>
            <td>OK</td>
            <td>Edmond</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Galena</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Spring Lake</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Centerville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Pelham</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Shawnee</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Walla Walla</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>Ames</td>
        </tr>
        <tr>
            <td>WSX</td>
            <td>Midhurst</td>
        </tr>
        <tr>
            <td>ZH</td>
            <td>Greifensee</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Dexter</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Hampden</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Clemmons</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Burke</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Avondale</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Peru</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Evansville</td>
        </tr>
        <tr>
            <td>GU</td>
            <td>Guatemala City</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Monitor</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Chester</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Brick</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Mount Vernon</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>East Andover</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Winona</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Loveland</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Oceanside</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Highlands</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Reedville</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Ascot Vale</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Chatsworth</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Mateo</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Worcester</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Ashburn</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Oakdale</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Tubac</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Corona</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Canton</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Binghamton</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Irving</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>San Antonio</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Parsippany</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Pompano Beach</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Azusa</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Cabot</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Claremont</td>
        </tr>
        <tr>
            <td>BY</td>
            <td>Moosen</td>
        </tr>
        <tr>
            <td>ME</td>
            <td>Bath</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Lincoln</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Utica</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Walnut Creek</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Wichita</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Hamden</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Corralitos</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Bowling Green</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Manitou Springs</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>East Haven</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Roanoke</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>La Mesa</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Chesapeake City</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>El Paso</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Bedminster</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Reisterstown</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Fayetteville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Ithaca</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Dingmans Ferry</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Umina Beach</td>
        </tr>
        <tr>
            <td>QC</td>
            <td>Chelsea</td>
        </tr>
        <tr>
            <td>HH</td>
            <td>Hamburg</td>
        </tr>
        <tr>
            <td>DE</td>
            <td>Rehoboth Bch</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Peoria</td>
        </tr>
        <tr>
            <td>KY</td>
            <td>Lexington</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Hosle</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>British Columbia</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Sudbury</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Broadway</td>
        </tr>
        <tr>
            <td>MT</td>
            <td>Livingston</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Riverside</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Royal Oak</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Carmel</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>Portland</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Salida</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>West Babylon</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Drammen</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Hamilton</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Denver</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Fairfax</td>
        </tr>
        <tr>
            <td>BNE</td>
            <td>London</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Hamilton</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Atlantic Beach</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Nesbru</td>
        </tr>
        <tr>
            <td>MB</td>
            <td>Winnipeg</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Newport Beach</td>
        </tr>
        <tr>
            <td>1</td>
            <td>Mjølkeråen</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Albany</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Atherton</td>
        </tr>
        <tr>
            <td>45</td>
            <td>Ravenna</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Far Hills</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Emeryville</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Richmond</td>
        </tr>
        <tr>
            <td>NV</td>
            <td>Reno</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Troy</td>
        </tr>
        <tr>
            <td>TM</td>
            <td>Timisoara</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Mahopac</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Fort Valley</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Weaverville</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Mount Vernon</td>
        </tr>
        <tr>
            <td>S</td>
            <td>Christchurch</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Mechanicsburg</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Brooksville</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Jupiter</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Floral Park</td>
        </tr>
        <tr>
            <td>MT</td>
            <td>Big Sky</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Chester</td>
        </tr>
        <tr>
            <td>CT</td>
            <td>New Milford</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Syracuse</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Hastings On Hudson</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Sugar Land</td>
        </tr>
        <tr>
            <td>62</td>
            <td>Rignano Flaminio</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Morris</td>
        </tr>
        <tr>
            <td>10</td>
            <td>Vennesla</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Franklin</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Bonaire</td>
        </tr>
        <tr>
            <td>UT</td>
            <td>Park City</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Mullica Hill</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Marina Del Rey</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Arvada</td>
        </tr>
        <tr>
            <td>DE</td>
            <td>Lewes</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Ossining</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Mount Airy</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Dulles</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Calimesa</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Rancho Santa Fe</td>
        </tr>
        <tr>
            <td>5</td>
            <td>Singapore</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>Spartanburg</td>
        </tr>
        <tr>
            <td>OR</td>
            <td>Beaverton</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Torrance</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Croton On Hudson</td>
        </tr>
        <tr>
            <td>HI</td>
            <td>Paia</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Antioch</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Bloomington</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Brecksville</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Bothell</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Green Valley</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Taunton</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Evanston</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Fredericksburg</td>
        </tr>
        <tr>
            <td>DE</td>
            <td>Wilmington</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Bowen Island</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Port Chester</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Dorchester</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>High Point</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Skillman</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Jamaica Plain</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Deerfield</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Short Hills</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>East Greenville</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Lafayette</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Miami Beach</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Forest Hills</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Salem</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Geneva</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Addison</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Modesto</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Dhahran</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Quinte Shores</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Qualicum Beach</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Verona</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>North Attleboro</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Dumfries</td>
        </tr>
        <tr>
            <td>RI</td>
            <td>West Kingston</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Bc</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Culver City</td>
        </tr>
        <tr>
            <td>KEN</td>
            <td>Bromley</td>
        </tr>
        <tr>
            <td>SC</td>
            <td>North Myrtle Beach</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Irvington</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>West Covina</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Levering</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Merion Station</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Mount Laurel</td>
        </tr>
        <tr>
            <td>WY</td>
            <td>Jackson</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Encinitas</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Lebanon</td>
        </tr>
        <tr>
            <td>VIC</td>
            <td>Parkdale</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Kanwal</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Vashon</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>League City</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Moelv</td>
        </tr>
        <tr>
            <td>NL</td>
            <td>Paradise</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Chestnut Hill</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Huntington Station</td>
        </tr>
        <tr>
            <td>AL</td>
            <td>Tuscumbia</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Seaford</td>
        </tr>
        <tr>
            <td>SP</td>
            <td>Atibaia</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Pawlet</td>
        </tr>
        <tr>
            <td>N/A</td>
            <td>N/A</td>
        </tr>
        <tr>
            <td>SD</td>
            <td>Rapid City</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Schererville</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Stowe</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Ashland</td>
        </tr>
        <tr>
            <td>KY</td>
            <td>Waddy</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Bound Brook</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Mesa</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Mead</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Cross Plains</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Lexington</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Pfafftown</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Burnsville</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Harris</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Wenatchee</td>
        </tr>
        <tr>
            <td>45</td>
            <td>Ferrara</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Winfield</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>East Longmeadow</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Venice</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Clinton</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Old Bridge</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Davis</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>West Chester</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Sparrow Bush</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Abington</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Vernon</td>
        </tr>
        <tr>
            <td>ACT</td>
            <td>N/A</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Oak Park</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Bahama</td>
        </tr>
        <tr>
            <td>ACT</td>
            <td>Sale</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Lafayette</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Los Osos</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Valparaiso</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>Iowa City</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Moorhead</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Sterling Heights</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Wellesley</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Moorpark</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Mount Vernon</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Fullerton</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Califon</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Oyster Bay</td>
        </tr>
        <tr>
            <td>8</td>
            <td>Skien</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Nanuet</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Mebane</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Johnstown</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Saint Cloud</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Huron</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Southampton</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Sedona</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Great Falls</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>North Fort Myers</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Gainesville</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Surrey</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>Fairfield</td>
        </tr>
        <tr>
            <td>None</td>
            <td>None</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Bradenton</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>North Bend</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Athens</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Augusta</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Roslyn</td>
        </tr>
        <tr>
            <td>NB</td>
            <td>Fredericton</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Murfreesboro</td>
        </tr>
        <tr>
            <td>WI</td>
            <td>Hubertus</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Edgewater</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Aldie</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Kent</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Napa</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Chattanooga</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Huntington Beach</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Comox</td>
        </tr>
        <tr>
            <td>BC</td>
            <td>Port Moody</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Harrisburg</td>
        </tr>
        <tr>
            <td>AB</td>
            <td>Lethbridge</td>
        </tr>
        <tr>
            <td>UT</td>
            <td>Utrecht</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Oslo</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Peoria</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Loveland</td>
        </tr>
        <tr>
            <td>AZ</td>
            <td>Tolleson</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Yonkers</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>San Rafael</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Davidsonville</td>
        </tr>
        <tr>
            <td>HE</td>
            <td>Lahntal</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Glendale</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Free Union</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Middle Village</td>
        </tr>
        <tr>
            <td>SRY</td>
            <td>Guildford</td>
        </tr>
        <tr>
            <td>AK</td>
            <td>Kotzebue</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Mount Lawley</td>
        </tr>
        <tr>
            <td>21</td>
            <td>Turin</td>
        </tr>
        <tr>
            <td>12</td>
            <td>Knarrevik</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Andover</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Tuckerton</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Roswell</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Perth</td>
        </tr>
        <tr>
            <td>ON</td>
            <td>Johnstown</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Medina</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Randleman</td>
        </tr>
        <tr>
            <td>SP</td>
            <td>Campinas</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Redlands</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Voorhees</td>
        </tr>
        <tr>
            <td>KS</td>
            <td>Lawrence</td>
        </tr>
        <tr>
            <td>ES</td>
            <td>Hki</td>
        </tr>
        <tr>
            <td>NS</td>
            <td>Halifax</td>
        </tr>
        <tr>
            <td>VT</td>
            <td>Shelburne</td>
        </tr>
        <tr>
            <td>TN</td>
            <td>Antioch</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Glendora</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Naperville</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Petaluma</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Winter Garden</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Ocoee</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Chesterfield</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Titusville</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Howey In The Hills</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Strongsville</td>
        </tr>
        <tr>
            <td>MN</td>
            <td>Duluth</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Downers Grove</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Lincoln</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sonoma</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Philomont</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Fishers</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Huntingdon</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Clermont</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Lakeside</td>
        </tr>
        <tr>
            <td>ME</td>
            <td>Westbrook</td>
        </tr>
        <tr>
            <td>KY</td>
            <td>Bowling Green</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Stevensville</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Gambier</td>
        </tr>
        <tr>
            <td>WA</td>
            <td>Bellevue</td>
        </tr>
        <tr>
            <td>IN</td>
            <td>Zionsville</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Smithfield</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Tehachapi</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Vermilion</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Friendswood</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Sebastopol</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Middle Island</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Hicksville</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Englewood</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Monument</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Bullard</td>
        </tr>
        <tr>
            <td>MI</td>
            <td>Richland</td>
        </tr>
        <tr>
            <td>NJ</td>
            <td>Middletown</td>
        </tr>
        <tr>
            <td>MD</td>
            <td>Annapolis</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Fort Worth</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Cashiers</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>Marion</td>
        </tr>
        <tr>
            <td>IA</td>
            <td>Knoxville</td>
        </tr>
        <tr>
            <td>NSW</td>
            <td>Farmborough Heights</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Navarre</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Folsom</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Georgetown</td>
        </tr>
        <tr>
            <td>ID</td>
            <td>Meridian</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Park Ridge</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Danville</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Temecula</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Los Altos</td>
        </tr>
        <tr>
            <td>MS</td>
            <td>Houston</td>
        </tr>
        <tr>
            <td>GA</td>
            <td>Decatur</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Shingle Springs</td>
        </tr>
        <tr>
            <td>TX</td>
            <td>Midland</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Collegeville</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Shelter Island</td>
        </tr>
        <tr>
            <td>CA</td>
            <td>Vallejo</td>
        </tr>
        <tr>
            <td>OH</td>
            <td>Pataskala</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>O Fallon</td>
        </tr>
        <tr>
            <td>ID</td>
            <td>Boise</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Palm Bay</td>
        </tr>
        <tr>
            <td>FL</td>
            <td>Morriston</td>
        </tr>
        <tr>
            <td>PA</td>
            <td>Wexford</td>
        </tr>
        <tr>
            <td>IL</td>
            <td>Macomb</td>
        </tr>
        <tr>
            <td>VA</td>
            <td>The Plains</td>
        </tr>
        <tr>
            <td>CO</td>
            <td>Glenwood Springs</td>
        </tr>
        <tr>
            <td>NY</td>
            <td>Franklin Square</td>
        </tr>
        <tr>
            <td>MA</td>
            <td>Salem</td>
        </tr>
        <tr>
            <td>NC</td>
            <td>Cornelius</td>
        </tr>
        <tr>
            <td>NH</td>
            <td>Wilmot</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">3999 rows, truncated to displaylimit of 1000</span>



If you examine the query output carefully, you will see that there are
many rows with California (CA) in the state column and four rows that
have Gainesville in the city column (Georgia, Arkansas, Florida, and
Virginia all have cities named Gainesville in our user table), but no
two rows have the same state and city combination.

When you use the DISTINCT clause with the LIMIT clause in a statement,
MySQL stops searching when it finds the number of *unique* rows
specified in the LIMIT clause, not when it goes through the number of
rows in the LIMIT clause.

For example, if the first 6 entries of the breed column in the dogs
table were:

| Labrador Retriever
| Shetland Sheepdog
| Golden Retriever
| Golden Retriever
| Shih Tzu
| Siberian Husky

The output of the following query:

.. code:: mysql

    SELECT DISTINCT breed
    FROM dogs LIMIT 5;

would be the first 5 different breeds:

| Labrador Retriever
| Shetland Sheepdog
| Golden Retriever
| Shih Tzu
| Siberian Husky

*not* the distinct breeds in the first 5 rows:

| Labrador Retriever
| Shetland Sheepdog
| Golden Retriever
| Shih Tzu

**Question 2: How would you list all the possible combinations of test
names and subcategory names in complete\_tests table? (If you do not
limit your output, you should retrieve 45 possible combinations)**

.. code:: ipython3

    %%sql 
    SELECT DISTINCT test_name, subcategory_name 
    FROM complete_tests;


.. parsed-literal::

    45 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>test_name</th>
            <th>subcategory_name</th>
        </tr>
        <tr>
            <td>Yawn Warm-up</td>
            <td>Empathy</td>
        </tr>
        <tr>
            <td>Yawn Game</td>
            <td>Empathy</td>
        </tr>
        <tr>
            <td>Eye Contact Warm-up</td>
            <td>Empathy</td>
        </tr>
        <tr>
            <td>Eye Contact Game</td>
            <td>Empathy</td>
        </tr>
        <tr>
            <td>Treat Warm-up</td>
            <td>Communication</td>
        </tr>
        <tr>
            <td>Arm Pointing</td>
            <td>Communication</td>
        </tr>
        <tr>
            <td>Foot Pointing</td>
            <td>Communication</td>
        </tr>
        <tr>
            <td>Watching</td>
            <td>Cunning</td>
        </tr>
        <tr>
            <td>Turn Your Back</td>
            <td>Cunning</td>
        </tr>
        <tr>
            <td>Cover Your Eyes</td>
            <td>Cunning</td>
        </tr>
        <tr>
            <td>Watching - Part 2</td>
            <td>Cunning</td>
        </tr>
        <tr>
            <td>One Cup Warm-up</td>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Two Cup Warm-up</td>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Memory versus Pointing</td>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Memory versus Smell</td>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Delayed Cup Game</td>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Inferential Reasoning Warm-up</td>
            <td>Reasoning</td>
        </tr>
        <tr>
            <td>Inferential Reasoning Game</td>
            <td>Reasoning</td>
        </tr>
        <tr>
            <td>Physical Reasoning Warm-up</td>
            <td>Reasoning</td>
        </tr>
        <tr>
            <td>Physical Reasoning Game</td>
            <td>Reasoning</td>
        </tr>
        <tr>
            <td>Navigation Warm-up</td>
            <td>Spatial Navigation</td>
        </tr>
        <tr>
            <td>Navigation Learning</td>
            <td>Spatial Navigation</td>
        </tr>
        <tr>
            <td>Navigation Game</td>
            <td>Spatial Navigation</td>
        </tr>
        <tr>
            <td>Impossible Task Warm-up</td>
            <td>Impossible Task</td>
        </tr>
        <tr>
            <td>Impossible Task Game</td>
            <td>Impossible Task</td>
        </tr>
        <tr>
            <td>Numerosity Warm-Up</td>
            <td>Numerosity</td>
        </tr>
        <tr>
            <td>5 vs 1 Game</td>
            <td>Numerosity</td>
        </tr>
        <tr>
            <td>3 vs 1 Game</td>
            <td>Numerosity</td>
        </tr>
        <tr>
            <td>Warm-Up</td>
            <td>Social Bias</td>
        </tr>
        <tr>
            <td>1 vs 1 Game</td>
            <td>Social Bias</td>
        </tr>
        <tr>
            <td>5 vs 1 Game</td>
            <td>Social Bias</td>
        </tr>
        <tr>
            <td>Warm-up</td>
            <td>Smell Game</td>
        </tr>
        <tr>
            <td>Smell Game</td>
            <td>Smell Game</td>
        </tr>
        <tr>
            <td>Warm-Up</td>
            <td>Shell Game</td>
        </tr>
        <tr>
            <td>Switch</td>
            <td>Shell Game</td>
        </tr>
        <tr>
            <td>Slide</td>
            <td>Shell Game</td>
        </tr>
        <tr>
            <td>Warm-Up</td>
            <td>Self Control Game</td>
        </tr>
        <tr>
            <td>Self Control Game</td>
            <td>Self Control Game</td>
        </tr>
        <tr>
            <td>Warm-Up</td>
            <td>Expression Game</td>
        </tr>
        <tr>
            <td>Expression Game</td>
            <td>Expression Game</td>
        </tr>
        <tr>
            <td>Different Perspective</td>
            <td>Perspective Game</td>
        </tr>
        <tr>
            <td>Shared Perspective</td>
            <td>Perspective Game</td>
        </tr>
        <tr>
            <td>Stair Game</td>
            <td>Laterality</td>
        </tr>
        <tr>
            <td>Shaker Warm-Up</td>
            <td>Shaker Game</td>
        </tr>
        <tr>
            <td>Shaker Game</td>
            <td>Shaker Game</td>
        </tr>
    </table>



3. Use ORDER BY to sort the output of your query
------------------------------------------------

As you might have noticed already when examining the output of the
queries you have executed thus far, databases do not have built-in
sorting mechanisms that automatically sort the output of your query.
However, SQL permits the use of the powerful ORDER BY clause to allow
you to sort the output according to your own specifications. Let's look
at how you would implement a simple ORDER BY clause.

Recall our query outline:

Your ORDER BY clause will come after everything else in the main part of
your query, but before a LIMIT clause.

If you wanted the breeds of dogs in the dog table sorted in alphabetical
order, you could query:

.. code:: mysql

    SELECT DISTINCT breed
    FROM dogs 
    ORDER BY breed

**Try it yourself:**

.. code:: ipython3

    %%sql
    SELECT DISTINCT breed
    FROM dogs 
    ORDER BY breed;


.. parsed-literal::

    2006 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>breed</th>
        </tr>
        <tr>
            <td>-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>-Beagle Mix</td>
        </tr>
        <tr>
            <td>-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>-Border Collie Mix</td>
        </tr>
        <tr>
            <td>-Boxer Mix</td>
        </tr>
        <tr>
            <td>-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>-Collie Mix</td>
        </tr>
        <tr>
            <td>-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>-Great Dane Mix</td>
        </tr>
        <tr>
            <td>-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>-Maltese Mix</td>
        </tr>
        <tr>
            <td>-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>-Otterhound Mix</td>
        </tr>
        <tr>
            <td>-Polish Lowland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>-Poodle Mix</td>
        </tr>
        <tr>
            <td>-Pug Mix</td>
        </tr>
        <tr>
            <td>-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>-Whippet Mix</td>
        </tr>
        <tr>
            <td>-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher</td>
        </tr>
        <tr>
            <td>Affenpinscher-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Brussels Griffon Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Poodle Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Spanish Water Dog Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound</td>
        </tr>
        <tr>
            <td>Afghan Hound-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Akita Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Portuguese Podengo Pequeno Mix</td>
        </tr>
        <tr>
            <td>Akita</td>
        </tr>
        <tr>
            <td>Akita- Mix</td>
        </tr>
        <tr>
            <td>Akita-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Akita-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Akita-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Akita-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Akita-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Akita-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute</td>
        </tr>
        <tr>
            <td>Alaskan Malamute- Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Beagle Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Collie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound</td>
        </tr>
        <tr>
            <td>American English Coonhound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog</td>
        </tr>
        <tr>
            <td>American Eskimo Dog- Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Papillon Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Foxhound</td>
        </tr>
        <tr>
            <td>American Foxhound- Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Pointer Mix</td>
        </tr>
        <tr>
            <td>American Hairless Terrier</td>
        </tr>
        <tr>
            <td>American Hairless Terrier-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>American Leopard Hound</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier- Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Brittany Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cane Corso Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Greyhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Plott Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Pointer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Treeing Tennessee Brindle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Vizsla Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier- Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogo Argentino Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Wirehaired Pointer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Gordon Setter Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Greyhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Miniature Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Neapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Portuguese Podengo Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>American Water Spaniel</td>
        </tr>
        <tr>
            <td>American Water Spaniel-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde- Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog- Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Curly-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Longhaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Labradoodle</td>
        </tr>
        <tr>
            <td>Australian Labradoodle-Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd</td>
        </tr>
        <tr>
            <td>Australian Shepherd- Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Beagle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pug Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier</td>
        </tr>
        <tr>
            <td>Australian Terrier-Lowchen Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Barbet</td>
        </tr>
        <tr>
            <td>Basenji</td>
        </tr>
        <tr>
            <td>Basenji- Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-Beagle Mix</td>
        </tr>
        <tr>
            <td>Basenji-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basenji-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Basenji-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Basenji-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Basenji-Whippet Mix</td>
        </tr>
        <tr>
            <td>Basset Hound</td>
        </tr>
        <tr>
            <td>Basset Hound- Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pointer Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Poodle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle</td>
        </tr>
        <tr>
            <td>Beagle- Mix</td>
        </tr>
        <tr>
            <td>Beagle-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boxer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Collie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Beagle-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pointer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Poodle Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pug Mix</td>
        </tr>
        <tr>
            <td>Beagle-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Beagle-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Beagle-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Whippet Mix</td>
        </tr>
        <tr>
            <td>Beaglier</td>
        </tr>
        <tr>
            <td>Bearded Collie</td>
        </tr>
        <tr>
            <td>Bearded Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Soft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Tibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Beauceron</td>
        </tr>
        <tr>
            <td>Beauceron-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Belgian Laekenois Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>Belgian Laekenois</td>
        </tr>
        <tr>
            <td>Belgian Malinois</td>
        </tr>
        <tr>
            <td>Belgian Malinois- Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog- Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Basenji Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Whippet Mix</td>
        </tr>
        <tr>
            <td>Bergamasco-Old English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Berger Picard</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Greater Swiss Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise</td>
        </tr>
        <tr>
            <td>Bichon Frise- Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Chinese Crested Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Havanese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Maltese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Poodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound- Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Plott Mix</td>
        </tr>
        <tr>
            <td>Black Russian Terrier</td>
        </tr>
        <tr>
            <td>Bloodhound</td>
        </tr>
        <tr>
            <td>Bloodhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Pointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boerboel</td>
        </tr>
        <tr>
            <td>Bolognese</td>
        </tr>
        <tr>
            <td>Border Collie</td>
        </tr>
        <tr>
            <td>Border Collie- Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Akita Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beauceron Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Borzoi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Brittany Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Field Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Icelandic Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Keeshond Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Kooikerhondje Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Saluki Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Soft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Welsh Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Whippet Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier</td>
        </tr>
        <tr>
            <td>Border Terrier- Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Lakeland Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Borzoi</td>
        </tr>
        <tr>
            <td>Borzoi-Whippet Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Danish-Swedish Farmdog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Boxer</td>
        </tr>
        <tr>
            <td>Boxer- Mix</td>
        </tr>
        <tr>
            <td>Boxer-Akita Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Boxer-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Boxer-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Boxer-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Ibizan Hound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Jindo Mix</td>
        </tr>
        <tr>
            <td>Boxer-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Poodle Mix</td>
        </tr>
        <tr>
            <td>Boxer-Pug Mix</td>
        </tr>
        <tr>
            <td>Boxer-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Boxer-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Boxer-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Boxer-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Vizsla Mix</td>
        </tr>
        <tr>
            <td>Boxer-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel</td>
        </tr>
        <tr>
            <td>Boykin Spaniel- Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Deutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Braque du Bourbonnais</td>
        </tr>
        <tr>
            <td>Briard</td>
        </tr>
        <tr>
            <td>Brittany</td>
        </tr>
        <tr>
            <td>Brittany-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Brittany-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Brittany-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Brittany-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Poodle Mix</td>
        </tr>
        <tr>
            <td>Brittany-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Poodle Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Pug Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bugg</td>
        </tr>
        <tr>
            <td>Bull Terrier</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>BullBoxer</td>
        </tr>
        <tr>
            <td>Bulldog</td>
        </tr>
        <tr>
            <td>Bulldog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Dogo Argentino Mix</td>
        </tr>
        <tr>
            <td>Bulldog-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Neapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Pug Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Wirehaired Pointing Griffon Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff</td>
        </tr>
        <tr>
            <td>Bullmastiff- Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Australian Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Canaan Dog</td>
        </tr>
        <tr>
            <td>Canaan Dog- Mix</td>
        </tr>
        <tr>
            <td>Cane Corso</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog- Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Plott Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Pointer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Caucasian Ovcharka</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Coton de Tulear Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Maltese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Papillon Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cesky Terrier</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Beagle Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Chihuahua</td>
        </tr>
        <tr>
            <td>Chihuahua- Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Australian Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Beagle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Chinese Crested Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Maltese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Norwich Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Papillon Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pug Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Whippet Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Xoloitzcuintli Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested</td>
        </tr>
        <tr>
            <td>Chinese Crested-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Maltese Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Papillon Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Pug Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei- Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Boerboel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Pug Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinook</td>
        </tr>
        <tr>
            <td>Chinook-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow</td>
        </tr>
        <tr>
            <td>Chow Chow-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Collie Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Keeshond Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Norfolk Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Cirneco dell&quot;Etna</td>
        </tr>
        <tr>
            <td>Clumber Spaniel</td>
        </tr>
        <tr>
            <td>Clumber Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cockapoo</td>
        </tr>
        <tr>
            <td>Cocker Spaniel</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Boxer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Maltese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pug Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Tibetan Spaniel Mix</td>
        </tr>
        <tr>
            <td>Collie</td>
        </tr>
        <tr>
            <td>Collie- Mix</td>
        </tr>
        <tr>
            <td>Collie-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Collie-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Belgian Malinois Mix</td>
        </tr>
        <tr>
            <td>Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Poodle Mix</td>
        </tr>
        <tr>
            <td>Curly-Coated Retriever</td>
        </tr>
        <tr>
            <td>Czechoslovakian Vlcak</td>
        </tr>
        <tr>
            <td>Dachshund</td>
        </tr>
        <tr>
            <td>Dachshund- Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Beagle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Black Russian Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Glen of Imaal Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Maltese Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Poodle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pug Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Scottish Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian</td>
        </tr>
        <tr>
            <td>Dalmatian-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Beagle Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog-Czechoslovakian Vlcak Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund- Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beagle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beauceron Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Boxer Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Poodle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Pug Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Dogo Argentino</td>
        </tr>
        <tr>
            <td>Dogo Argentino-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Boxer Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Drentsche Patrijshond</td>
        </tr>
        <tr>
            <td>Dutch Shepherd</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Appenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Foxhound</td>
        </tr>
        <tr>
            <td>English Foxhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter</td>
        </tr>
        <tr>
            <td>English Setter- Mix</td>
        </tr>
        <tr>
            <td>English Setter-Beagle Mix</td>
        </tr>
        <tr>
            <td>English Setter-Border Collie Mix</td>
        </tr>
        <tr>
            <td>English Setter-Brittany Mix</td>
        </tr>
        <tr>
            <td>English Setter-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>English Setter-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Setter-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter-Pointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel</td>
        </tr>
        <tr>
            <td>English Springer Spaniel- Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Border Collie Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Pointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>English Toy Spaniel</td>
        </tr>
        <tr>
            <td>Entlebucher Mountain Dog</td>
        </tr>
        <tr>
            <td>Estrela Mountain Dog</td>
        </tr>
        <tr>
            <td>Eurasier</td>
        </tr>
        <tr>
            <td>Field Spaniel</td>
        </tr>
        <tr>
            <td>Finnish Lapphund</td>
        </tr>
        <tr>
            <td>Finnish Spitz</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever- Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Irish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Portuguese Water Dog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog</td>
        </tr>
        <tr>
            <td>French Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Bulldog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Havanese Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Pug Mix</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">2006 rows, truncated to displaylimit of 1000</span>



(You might notice that some of the breeds start with a hyphen; we'll
come back to that later.)

The default is to sort the output in ascending order. However, you can
tell SQL to sort the output in descending order as well:

.. code:: mysql

    SELECT DISTINCT breed
    FROM dogs 
    ORDER BY breed DESC

Combining ORDER BY with LIMIT gives you an easy way to select the "top
10" and "last 10" in a list or column. For example, you could select the
User IDs and Dog IDs of the 5 customer-dog pairs who spent the least
median amount of time between their Dognition tests:

.. code:: mysql

    SELECT DISTINCT user_guid, median_ITI_minutes
    FROM dogs 
    ORDER BY median_ITI_minutes
    LIMIT 5

or the greatest median amount of time between their Dognition tests:

.. code:: mysql

    SELECT DISTINCT user_guid, median_ITI_minutes
    FROM dogs 
    ORDER BY median_ITI_minutes DESC
    LIMIT 5

You can also sort your output based on a derived field. If you wanted
your inter-test interval to be expressed in seconds instead of minutes,
you could incorporate a derived column and an alias into your last query
to get the 5 customer-dog pairs who spent the greatest median amount of
time between their Dognition tests in seconds:

.. code:: mysql

    SELECT DISTINCT user_guid, (median_ITI_minutes * 60) AS median_ITI_sec
    FROM dogs 
    ORDER BY median_ITI_sec DESC
    LIMIT 5

Note that the parentheses are important in that query; without them, the
database would try to make an alias for 60 instead of
median\_ITI\_minutes \* 60.

SQL queries also allow you to sort by multiple fields in a specified
order, similar to how Excel allows to include multiple levels in a sort
(see image below):

To achieve this in SQL, you include all the fields (or aliases) by which
you want to sort the results after the ORDER BY clause, separated by
commas, in the order you want them to be used for sorting. You can then
specify after each field whether you want the sort using that field to
be ascending or descending.

If you wanted to select all the distinct User IDs of customers in the
United States (abbreviated "US") and sort them according to the states
they live in in alphabetical order first, and membership type second,
you could query:

.. code:: mysql

    SELECT DISTINCT user_guid, state, membership_type
    FROM users
    WHERE country="US"
    ORDER BY state ASC, membership_type ASC

**Go ahead and try it yourself (if you do not limit the output, you
should get 9356 rows in your output):**

.. code:: ipython3

    %%sql 
    SELECT DISTINCT user_guid, state, membership_type
    FROM users 
    WHERE country="US"
    ORDER BY state DESC, membership_type DESC;


.. parsed-literal::

    9356 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>user_guid</th>
            <th>state</th>
            <th>membership_type</th>
        </tr>
        <tr>
            <td>ce80b888-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce986fdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7980f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c7066-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce13750c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce287aec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dc6c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74375c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74a85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d4d4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ef872-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fd49a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8377d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d6de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79ae30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce2c3da8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce770dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d199e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8164a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce324fc2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3cd8fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d4e9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dcae8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72e4ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce731ad4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754250-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d6016-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dc0f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd4d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce820076-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82452c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce876232-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971970-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9724d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce976c22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80b630-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce3eca4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6d03a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6dec62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7db9c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce82a24c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce978d88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce255c54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce258d00-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277624-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce286868-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce33a30e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3cf828-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3ebd16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce665d30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e92ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6f4698-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce701078-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fa74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fcc2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce711158-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce72ed16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce75732e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce761d7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce781750-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7976ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a1adc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c6abc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce872bdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce9686ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce979f1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce22414a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2267a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce244eb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2548e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2631d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce270360-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce28b5f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce295d72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2cabee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce337e06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce33d6b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f96aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4746b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4755ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66f3da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6772ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c3250-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c3fc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cc7e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ccb0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ce178-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cecf4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d4b72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5d88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ddb82-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e13cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e9b76-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ecd80-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f5c5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f6060-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fecd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70220c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7035d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce704804-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f628-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce711342-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce717b5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7250fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72f07c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72f73e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce730134-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73298e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce736a16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73ddc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7460c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7479d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74d270-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74d75c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74fcb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74fe3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce774852-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce776d46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce777a66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce78cae2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce799788-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79f85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a6906-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b1d7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b9b78-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bc954-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beab0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beb46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c4e2e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c6698-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cec62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d3424-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d4806-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dbcf0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7eb362-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7eb8c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80a320-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce814fbe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81ba4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d088-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8207e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82ba3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82c90c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82cb14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830200-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830bd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce831416-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce833c66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce839c92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8642e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86f4aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8703d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8755e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce896ad2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c2bb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce963910-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96ba84-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96fb52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971f4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9769e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98068c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98e55c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a690e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8040ec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce2e6b46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>4</td>
        </tr>
        <tr>
            <td>ce2941d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3f963c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce66539e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce70eec6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce731692-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce754912-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce79cece-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7bf258-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7dc89e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce889bf2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8a9808-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce916e9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce95bada-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce98d31e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9ae44c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce136ac6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce136c24-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce137700-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1381c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1387cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2203f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce23e4a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce240a8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce241ccc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce246a06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce249922-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24c5be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce250d26-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce255146-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25b014-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25f0c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce261cfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce261fa4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2698d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26a064-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26def8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce274e6a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27659e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce280f8a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28441e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce284ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28c448-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28cc5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2937ca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce296b14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29818a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29b4b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a0038-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a4b4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a8328-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c4046-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c7bce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2da4f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dd0b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce370ef4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3d27ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3dac50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3de0b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3deecc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3df8fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f8e1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3fd2aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce40dd9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce411192-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce472532-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6c8aa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e8fa0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6eda96-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ee64e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ef4c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fc55a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70520e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70624e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fc5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7106ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce716518-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73a6de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73d01e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73f6e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74670e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74b2fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74fad4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7549d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7551be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce765b9a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce765bfe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce766f5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7689ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79c924-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79f34a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a246e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7bfe06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c749e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c7ba6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cc160-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d2f56-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7dc09c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7e10ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7eadf4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7ee2e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f33f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f4a02-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce809c4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8232f8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce838004-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce83a02a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce841d52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce86a18a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce89196a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce896dac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce948dd6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce94f500-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97f7a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce987c66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce98c46e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce13615c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce136a1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2207de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce223c22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce254ab6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce254bce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce259534-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce259dd6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25bc12-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26073a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261a40-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce269308-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26dfb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277782-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce284b1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2866f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce286cbe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce287fba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce28c394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a874c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a8c38-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9264-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a993a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2ad42c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2b6ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2dc77c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2de31a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2e4f44-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce338d42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce36f4dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3b3aba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c533c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d5ca0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d5f84-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d6bb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e298c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f044c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f605e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4064c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce408024-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e11c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce663bca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66e9c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c4e2a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e10c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e1516-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e17a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e1a34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e5b02-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e7a1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e8e88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ed122-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ee374-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f7050-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f9d28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fb3a8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702270-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702568-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702cca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce703dfa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7056c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce708ea4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70a506-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70aba0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70be92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70cd7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f1c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce715f00-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce716b9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71a3c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71f500-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7205b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7290fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72c462-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73211e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce734112-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce734c16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce735648-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7395c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73a7f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73c54c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73d078-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73f1d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce740048-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74159c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74165a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741948-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74352c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce747852-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce747b36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7495c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74dd60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754c8c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757734-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75dc1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce762292-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce765adc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7673c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce767d32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76f06e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce776e04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce784356-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce78c902-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79198e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce798edc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79ccee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a1a14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a51aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a8166-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a83be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a85b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aa132-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b0096-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b17fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7b5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b99e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b9d6c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bcd28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd7fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd8c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bdd54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bf578-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bfb40-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bfcd0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c00ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c46d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c4d70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c5522-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c7e58-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cad7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cddbc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ce2b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cf0ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7db5b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7db66a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dbc32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dca1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e08c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e302c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e35b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e8388-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e9030-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e97d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ea1f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ecc26-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f589e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fb6a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80d2dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8127b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce821872-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce821c50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce829482-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b656-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce83c8e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce844d86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8669b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce867bec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8682fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8686aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86f02c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce881056-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce881290-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce890542-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce897ae0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce897b4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8a3aca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8be08c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c1f3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce91b12e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce920c3c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce92e8aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce92f8d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce934b60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9356c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce935a10-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce936b04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce936b5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce947d5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce967808-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce975e62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce976510-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce987dec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce995b5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99b946-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99c9ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99d37c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a45aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a5f36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9ac048-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ec8b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce261edc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28b0fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ed97e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7400a2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce743810-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce773948-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce788dde-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79d1d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2259d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce225b4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25a11e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce262f8a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce27bf9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce289ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a6b22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f828e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7101b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7120d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7177ec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7210c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7212a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72cc50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74f480-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757388-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce774b36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7965d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c7188-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e320c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce837532-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce85297c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86d8e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96ed4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98716c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99e2f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fb82a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce81536a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce3e34d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce401d64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce40e4b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce46e658-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce5c1b54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6c330e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6d483e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6dae3c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6de6c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6fe6fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce70808a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce710a32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce716a7c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72de7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7362fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce73b674-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce74a44e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7e9ad0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce85307a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce889ee0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8c1dea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96b908-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce99d732-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce136f94-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1377b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce221a76-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce225df6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24181c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2419de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24ea6c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce251b4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25482c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2578ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25f772-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce262300-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26639c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26681a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2697a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26b3ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26bedc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27603a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2771b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277566-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277bf6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2783b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce278a9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2790a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27de3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27e6ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27e7da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27efd2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27f40a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27fd42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce280530-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2839f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2844dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce286408-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2868c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28b282-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29a43a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29d34c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c0eaa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce34a5b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3e013c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3e739c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f65c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f8e80-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3fea06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce4032cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407a2a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407c6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407d90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce411aa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce470e30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce5c250e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce66491c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce665042-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6cb662-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e819a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6f53cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fd64e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fd9be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70353a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70859e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce720dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7280b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce733d20-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7341c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce734d2e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73fae4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74640c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce769628-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce769ee8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce76d05c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce76d66a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce77504a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce775cb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce78554e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7863ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce788f6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7919f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a952a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7accd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7ad652-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7b7e5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cd394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cf4dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7e34fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f4052-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f5bfa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce802f44-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce80715c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce83b40c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce84b65e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce876976-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce878dfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce89bb72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8ad48a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8b68e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce95f874-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97884c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce980330-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce980ea2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce98679e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2437de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce246830-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24a8e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24b5d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24cac8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2508bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25563c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce257cd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25c1da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25fbdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25fe70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261590-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261e1e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce266400-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26e90c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce275428-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277214-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277a20-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2781d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2812a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce285026-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2893b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce29675e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce299a1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a8b16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a90d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9c32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9f0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2aca22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2ad134-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2b1e28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2d6818-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2dc9a2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce30f71c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce322858-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce334a08-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3397b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce34c69e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce34fc86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce35448e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce354b1e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce35c490-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3875e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a8fa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a9182-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a92fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c4004-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c4b30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d1eb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d265e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d520a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e0f7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e3792-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e49d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e4ce6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e4eda-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e7630-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f803e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f9f6a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce401b70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce405dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40e56e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40e802-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40ecee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40ed48-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4102e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4112c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4158a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4166f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4179ca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce458556-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e5cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e86a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce472064-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce478ac2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6645d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66554c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce677710-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c7bfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cd2d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ce6b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cf0a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cf47e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d05c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d27e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d513a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5248-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d6d14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6da180-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dd6dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6de8e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e0562-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e0cd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e8ba4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6edaf0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f08ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f31ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f6006-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f724e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f7758-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f8748-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fb27c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fc280-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fdf4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce701bb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce701cda-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce707c52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce709070-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70962e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70bd7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70ec64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f16e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70fad8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce710776-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71152c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce715b4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7171ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce717530-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71759e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71814c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce718da4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71a58c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71df34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71eb64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72025c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce721558-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7242e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce724e10-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72537e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce726c74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72b562-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72b7e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72c4bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72e3fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72fd42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce732d3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce736994-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73897e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7389d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73978e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce739c34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73b78c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73f3a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7405e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741a60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741c2c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce742140-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74224e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74a50c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74ef3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7503f8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce750a74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7544ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754552-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce759502-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75b6b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7601a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76085c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce765794-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce766338-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce768f8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7860f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7961c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce797942-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce797abe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79b6d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79eb5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a0560-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a5b82-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a7d74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aa0ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7acc0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aefac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7cd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7eb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bcf12-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bdaac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bedb2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beede-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bf640-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c1148-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c1d6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c3786-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c80a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c93e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ce24e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d619c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dcee8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd23a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd82a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e9e90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ea156-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ece1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ed892-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f0b0a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f8440-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fd1fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80107c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce809efc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce816fd0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81a432-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d6aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82853c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce829978-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b340-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82c2e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830db8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce833f18-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce837afa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce842392-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8430a8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84aa92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84ac04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84c1bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84d0b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8516d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce852cce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86924e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce87f7f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce883e96-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8865c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce928e5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9359b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9368b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9492fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce95fde2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9690a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96a74c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9700d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971218-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97a2a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97acb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97e63e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f73c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f8c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce980272-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce982338-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98502e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98cc34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d80a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98fed4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce993070-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce993df4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce994434-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce994b32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce997b16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99f906-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a3fa6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a480c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9ae4b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76d3a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce244918-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce271d50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce33b2e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce66bf0a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6d6148-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a3e04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d6322-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce80c24c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce90fb4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97aa16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25aa9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce269114-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce278ce0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3308a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f713e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3fda8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce400dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4052ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce663e0e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5ea0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d7836-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d8236-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ece98-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ed406-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f9c56-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71b090-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce725040-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72581a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce728ad8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce735b7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7431da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75fe3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce772aca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79d6e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e8068-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d718-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81f798-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b084-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce839472-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84fc36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8a6dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c077e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce921aba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce932f68-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce961944-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce969a86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f32c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce980452-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d616-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce996036-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a6ca6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2bf226-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>4</td>
        </tr>
        <tr>
            <td>ce280404-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3a7e90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3fe646-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce4125b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce47172c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6662da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6e3352-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6eecd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce705722-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce71384a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7270c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7285e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72d894-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72db28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72f5d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7402d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce740f5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce757a18-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7adbc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7b7378-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7cf3ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7e71fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7eb16e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce822f88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce83b34e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce844836-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8534e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce854c54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce86f9f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce885cb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce894494-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8998cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce957f0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9685f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96b84a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96ef86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce99ae74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9a1760-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9a5ba8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce139bea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce22203e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2260e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24476a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce244be8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24d248-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce250e48-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce258256-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25900c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25bb54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce264330-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26e5b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2756da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27cfde-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce281c64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce285f58-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2863ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28806e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29d9a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2ad71a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2afa7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dad5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dcfb0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dd910-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2e14c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">9356 rows, truncated to displaylimit of 1000</span>



You might notice that some of the rows have null values in the state
field. You could revise your query to only select rows that do not have
null values in either the state or membership\_type column:

.. code:: mysql

    SELECT DISTINCT user_guid, state, membership_type
    FROM users
    WHERE country="US" AND state IS NOT NULL and membership_type IS NOT NULL
    ORDER BY state ASC, membership_type ASC

**Question 3: Below, try executing a query that would sort the same
output as described above by membership\_type first in descending order,
and state second in ascending order:**

.. code:: ipython3

    %%sql 
    SELECT DISTINCT user_guid, state, membership_type
    FROM users 
    WHERE country="US" AND state IS NOT NULL AND membership_type IS NOT NULL
    ORDER BY state DESC, membership_type DESC;


.. parsed-literal::

    9356 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>user_guid</th>
            <th>state</th>
            <th>membership_type</th>
        </tr>
        <tr>
            <td>ce80b888-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce986fdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7980f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c7066-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce13750c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce287aec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dc6c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74375c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74a85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d4d4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ef872-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fd49a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8377d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d6de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WY</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79ae30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce2c3da8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce770dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d199e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8164a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce324fc2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3cd8fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d4e9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dcae8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72e4ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce731ad4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754250-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d6016-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dc0f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd4d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce820076-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82452c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce876232-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971970-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9724d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce976c22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WV</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80b630-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce3eca4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6d03a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6dec62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7db9c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce82a24c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce978d88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce255c54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce258d00-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277624-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce286868-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce33a30e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3cf828-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3ebd16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce665d30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e92ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6f4698-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce701078-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fa74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fcc2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce711158-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce72ed16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce75732e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce761d7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce781750-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7976ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a1adc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c6abc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce872bdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce9686ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce979f1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce22414a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2267a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce244eb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2548e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2631d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce270360-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce28b5f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce295d72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2cabee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce337e06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce33d6b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f96aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4746b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4755ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66f3da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6772ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c3250-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c3fc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cc7e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ccb0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ce178-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cecf4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d4b72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5d88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ddb82-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e13cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e9b76-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ecd80-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f5c5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f6060-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fecd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70220c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7035d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce704804-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f628-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce711342-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce717b5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7250fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72f07c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72f73e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce730134-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73298e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce736a16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73ddc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7460c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7479d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74d270-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74d75c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74fcb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74fe3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce774852-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce776d46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce777a66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce78cae2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce799788-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79f85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a6906-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b1d7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b9b78-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bc954-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beab0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beb46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c4e2e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c6698-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cec62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d3424-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d4806-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dbcf0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7eb362-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7eb8c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80a320-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce814fbe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81ba4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d088-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8207e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82ba3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82c90c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82cb14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830200-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830bd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce831416-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce833c66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce839c92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8642e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86f4aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8703d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8755e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce896ad2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c2bb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce963910-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96ba84-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96fb52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971f4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9769e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98068c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98e55c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a690e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WI</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8040ec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce2e6b46-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>4</td>
        </tr>
        <tr>
            <td>ce2941d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3f963c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce66539e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce70eec6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce731692-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce754912-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce79cece-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7bf258-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7dc89e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce889bf2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8a9808-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce916e9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce95bada-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce98d31e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9ae44c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce136ac6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce136c24-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce137700-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1381c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1387cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2203f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce23e4a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce240a8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce241ccc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce246a06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce249922-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24c5be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce250d26-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce255146-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25b014-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25f0c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce261cfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce261fa4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2698d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26a064-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26def8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce274e6a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27659e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce280f8a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28441e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce284ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28c448-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28cc5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2937ca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce296b14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29818a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29b4b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a0038-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a4b4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2a8328-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c4046-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c7bce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2da4f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dd0b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce370ef4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3d27ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3dac50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3de0b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3deecc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3df8fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f8e1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3fd2aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce40dd9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce411192-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce472532-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6c8aa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e8fa0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6eda96-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ee64e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ef4c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fc55a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70520e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70624e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70fc5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7106ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce716518-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73a6de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73d01e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73f6e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74670e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74b2fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74fad4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7549d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7551be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce765b9a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce765bfe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce766f5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7689ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79c924-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79f34a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a246e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7bfe06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c749e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7c7ba6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cc160-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d2f56-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7dc09c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7e10ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7eadf4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7ee2e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f33f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f4a02-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce809c4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8232f8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce838004-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce83a02a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce841d52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce86a18a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce89196a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce896dac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce948dd6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce94f500-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97f7a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce987c66-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce98c46e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce13615c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce136a1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2207de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce223c22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce254ab6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce254bce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce259534-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce259dd6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25bc12-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26073a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261a40-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce269308-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26dfb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277782-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce284b1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2866f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce286cbe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce287fba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce28c394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a874c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a8c38-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9264-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a993a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2ad42c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2b6ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2dc77c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2de31a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2e4f44-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce338d42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce36f4dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3b3aba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c533c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d5ca0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d5f84-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d6bb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e298c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f044c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f605e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4064c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce408024-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e11c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce663bca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66e9c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c4e2a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e10c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e1516-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e17a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e1a34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e5b02-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e7a1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e8e88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ed122-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ee374-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f7050-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f9d28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fb3a8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702270-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702568-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce702cca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce703dfa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7056c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce708ea4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70a506-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70aba0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70be92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70cd7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f1c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce715f00-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce716b9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71a3c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71f500-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7205b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7290fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72c462-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73211e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce734112-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce734c16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce735648-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7395c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73a7f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73c54c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73d078-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73f1d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce740048-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74159c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74165a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741948-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74352c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce747852-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce747b36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7495c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74dd60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754c8c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757734-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75dc1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce762292-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce765adc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7673c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce767d32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76f06e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce776e04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce784356-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce78c902-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79198e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce798edc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79ccee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a1a14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a51aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a8166-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a83be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a85b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aa132-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b0096-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b17fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7b5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b99e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b9d6c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bcd28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd7fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd8c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bdd54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bf578-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bfb40-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bfcd0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c00ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c46d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c4d70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c5522-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c7e58-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cad7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cddbc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ce2b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7cf0ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7db5b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7db66a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dbc32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dca1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e08c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e302c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e35b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e8388-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e9030-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e97d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ea1f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ecc26-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f589e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fb6a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80d2dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8127b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce821872-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce821c50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce829482-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b656-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce83c8e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce844d86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8669b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce867bec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8682fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8686aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86f02c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce881056-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce881290-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce890542-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce897ae0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce897b4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8a3aca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8be08c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c1f3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce91b12e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce920c3c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce92e8aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce92f8d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce934b60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9356c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce935a10-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce936b04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce936b5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce947d5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce967808-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce975e62-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce976510-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce987dec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce995b5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99b946-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99c9ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99d37c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a45aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a5f36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9ac048-7144-11e5-ba71-058fbc01cf0b</td>
            <td>WA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ec8b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce261edc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28b0fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6ed97e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7400a2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce743810-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce773948-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce788dde-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce79d1d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2259d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce225b4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25a11e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce262f8a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce27bf9e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce289ce8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a6b22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f828e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7101b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7120d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7177ec-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7210c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7212a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72cc50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74f480-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757388-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce774b36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7965d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c7188-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e320c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce837532-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce85297c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86d8e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96ed4c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98716c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99e2f4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fb82a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce81536a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>5</td>
        </tr>
        <tr>
            <td>ce3e34d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce401d64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce40e4b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce46e658-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce5c1b54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6c330e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6d483e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6dae3c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6de6c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6fe6fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce70808a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce710a32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce716a7c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72de7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7362fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce73b674-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce74a44e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7e9ad0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce85307a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce889ee0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8c1dea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96b908-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce99d732-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce136f94-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce1377b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce221a76-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce225df6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24181c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2419de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24ea6c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce251b4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25482c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2578ba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25f772-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce262300-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26639c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26681a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2697a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26b3ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26bedc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27603a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2771b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277566-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce277bf6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2783b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce278a9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2790a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27de3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27e6ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27e7da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27efd2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27f40a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27fd42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce280530-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2839f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2844dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce286408-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2868c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28b282-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29a43a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29d34c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2c0eaa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce34a5b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3e013c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3e739c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f65c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3f8e80-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce3fea06-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce4032cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407a2a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407c6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce407d90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce411aa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce470e30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce5c250e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce66491c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce665042-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6cb662-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6e819a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6f53cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fd64e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6fd9be-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70353a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce70859e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce720dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7280b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce733d20-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7341c6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce734d2e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce73fae4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce74640c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce769628-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce769ee8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce76d05c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce76d66a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce77504a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce775cb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce78554e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7863ea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce788f6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7919f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a952a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7accd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7ad652-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7b7e5e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cd394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7cf4dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7e34fa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f4052-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7f5bfa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce802f44-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce80715c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce83b40c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce84b65e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce876976-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce878dfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce89bb72-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8ad48a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce8b68e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce95f874-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97884c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce980330-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce980ea2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce98679e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2437de-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce246830-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24a8e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24b5d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce24cac8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2508bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25563c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce257cd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25c1da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25fbdc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce25fe70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261590-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce261e1e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce266400-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce26e90c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce275428-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277214-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce277a20-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2781d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2812a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce285026-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2893b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce29675e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce299a1c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a8b16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a90d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9c32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2a9f0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2aca22-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2ad134-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2b1e28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2d6818-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2dc9a2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce30f71c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce322858-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce334a08-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3397b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce34c69e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce34fc86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce35448e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce354b1e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce35c490-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3875e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a8fa2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a9182-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3a92fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c4004-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3c4b30-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d1eb6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d265e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3d520a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e0f7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e3792-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e49d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e4ce6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e4eda-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3e7630-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f803e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f9f6a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce401b70-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce405dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40e56e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40e802-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40ecee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce40ed48-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4102e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4112c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4158a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4166f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4179ca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce458556-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e5cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce46e86a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce472064-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce478ac2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6645d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce66554c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce677710-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6c7bfc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cd2d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ce6b4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cf0a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6cf47e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d05c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d27e6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d513a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5248-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d6d14-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6da180-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6dd6dc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6de8e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e0562-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e0cd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6e8ba4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6edaf0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f08ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f31ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f6006-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f724e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f7758-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f8748-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fb27c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fc280-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6fdf4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce701bb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce701cda-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce707c52-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce709070-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70962e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70bd7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70ec64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70f16e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce70fad8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce710776-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71152c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce715b4a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7171ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce717530-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71759e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71814c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce718da4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71a58c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71df34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71eb64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72025c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce721558-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7242e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce724e10-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72537e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce726c74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72b562-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72b7e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72c4bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72e3fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72fd42-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce732d3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce736994-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73897e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7389d8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73978e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce739c34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73b78c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce73f3a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7405e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741a60-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce741c2c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce742140-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74224e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74a50c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce74ef3a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7503f8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce750a74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7544ee-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce754552-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce759502-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75b6b8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7601a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76085c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce765794-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce766338-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce768f8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7860f2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7961c8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce797942-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce797abe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79b6d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79eb5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a0560-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a5b82-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7a7d74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aa0ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7acc0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7aefac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7cd8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7b7eb8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bcf12-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bd85e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bdaac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bedb2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7beede-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7bf640-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c1148-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c1d6e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c3786-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c80a6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7c93e8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ce24e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7d619c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dcee8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd23a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7dd82a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e9e90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ea156-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ece1a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7ed892-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f0b0a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7f8440-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7fd1fc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce80107c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce809efc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce816fd0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81a432-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d394-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d6aa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82853c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce829978-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b340-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82c2e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce830db8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce833f18-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce837afa-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce842392-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8430a8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84aa92-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84ac04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84c1bc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84d0b2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8516d0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce852cce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce86924e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce87f7f6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce883e96-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8865c4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce928e5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9359b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9368b6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9492fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce95fde2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9690a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce96a74c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9700d4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce971218-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97a2a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97acb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97e63e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f73c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f8c2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce980272-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce982338-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98502e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98cc34-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d80a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98fed4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce993070-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce993df4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce994434-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce994b32-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce997b16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce99f906-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a3fa6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a480c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9ae4b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>VA</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce76d3a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce244918-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce271d50-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce33b2e0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce66bf0a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce6d6148-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7a3e04-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce7d6322-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce80c24c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce90fb4e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce97aa16-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25aa9c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce269114-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce278ce0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3308a4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3f713e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce3fda8e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce400dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce4052ac-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce663e0e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d5ea0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d7836-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6d8236-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ece98-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6ed406-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce6f9c56-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce71b090-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce725040-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce72581a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce728ad8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce735b7a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7431da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce757dc4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce75fe3e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce772aca-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce79d6e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce7e8068-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81d718-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce81f798-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce82b084-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce839472-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce84fc36-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8a6dce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce8c077e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce921aba-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce932f68-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce961944-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce969a86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce97f32c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce980452-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce98d616-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce996036-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce9a6ca6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>UT</td>
            <td>1</td>
        </tr>
        <tr>
            <td>ce2bf226-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>4</td>
        </tr>
        <tr>
            <td>ce280404-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3a7e90-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce3fe646-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce4125b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce47172c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6662da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6e3352-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce6eecd4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce705722-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce71384a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7270c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7285e2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72d894-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72db28-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce72f5d6-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7402d2-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce740f5c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce757a18-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7adbc0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7b7378-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7cf3ce-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7e71fe-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce7eb16e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce822f88-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce83b34e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce844836-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8534e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce854c54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce86f9f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce885cb4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce894494-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce8998cc-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce957f0c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9685f0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96b84a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce96ef86-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce99ae74-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9a1760-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce9a5ba8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ce139bea-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce22203e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2260e4-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24476a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce244be8-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce24d248-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce250e48-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce258256-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25900c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce25bb54-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce264330-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce26e5b0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2756da-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce27cfde-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce281c64-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce285f58-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2863ae-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce28806e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce29d9a0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2ad71a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2afa7e-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dad5a-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dcfb0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2dd910-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
        <tr>
            <td>ce2e14c0-7144-11e5-ba71-058fbc01cf0b</td>
            <td>TX</td>
            <td>2</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">9356 rows, truncated to displaylimit of 1000</span>



4. Export your query results to a text file
-------------------------------------------

Next week, we will learn how to complete some basic forms of data
analysis in SQL. However, if you know how to use other analysis or
visualization software like Excel or Tableau, you can implement these
analyses with the SQL skills you have gained already, as long as you can
export the results of your SQL queries in a format other software
packages can read. Almost every database interface has a different
method for exporting query results, so you will need to look up how to
do it every time you try a new interface (another place where having a
desire to learn new things will come in handy!).

There are two ways to export your query results using our Jupyter
interface.

1. You can select and copy the output you see in an output window, and
   paste it into another program. Although this strategy is very simple,
   it only works if your output is very limited in size (since you can
   only paste 1000 rows at a time).

2. You can tell MySQL to put the results of a query into a variable (for
   our purposes consider a variable to be a temporary holding place),
   and then use Python code to format the data in the variable as a CSV
   file (comma separated value file, a .CSV file) that can be
   downloaded. When you use this strategy, all of the results of a query
   will be saved into the variable, not just the first 1000 rows as
   displayed in Jupyter, even if we have set up Jupyter to only display
   1000 rows of the output.

Let's see how we could export query results using the second method.

To tell MySQL to put the results of a query into a variable, use the
following syntax:

    \`\`\`python variable\_name\_of\_your\_choice = %sql [your full
    query goes here];

::


    In this case, you must execute your SQL query all on one line.  So if you wanted to export the list of dog breeds in the dogs table, you could begin by executing:

    >```python
    breed_list = %sql SELECT DISTINCT breed FROM dogs ORDER BY breed;

**Go ahead and try it:**

.. code:: ipython3

    breed_list = %sql SELECT DISTINCT breed FROM dogs ORDER BY breed;


.. parsed-literal::

    2006 rows affected.


Once your variable is created, using the above command tell Jupyter to
format the variable as a csv file using the following syntax:

    \`\`\`python
    the\_output\_name\_you\_want.csv('the\_output\_name\_you\_want.csv')

::


    Since this line is being run in Python, do NOT include the %sql prefix when trying to execute the line.  We could therefore export the breed list by executing:

    >```python
    breed_list.csv('breed_list.csv')

When you do this, all of the results of the query will be saved in the
text file but the results will not be displayed in your notebook. This
is a convenient way to retrieve large amounts of data from a query
without taxing your browser or the server.

**Try it yourself:**

.. code:: ipython3

    breed_list.csv('breed_list.csv')




.. raw:: html

    <a href="./files/breed_list.csv">CSV results</a>



You should see a link in the output line that says "CSV results." You
can click on this link to see the text file in a tab in your browser or
to download the file to your computer (exactly how this works will
differ depending on your browser and settings, but your options will be
the same as if you were trying to open or download a file from any other
website.)

You can also open the file directly from the home page of your Jupyter
account. Behind the scenes, your csv file was written to your directory
on the Jupyter server, so you should now see this file listed in your
Jupyter account landing page along with the list of your notebooks. Just
like a notebook, you can copy it, rename it, or delete it from your
directory by clicking on the check box next to the file and clicking the
"duplicate," "rename," or trash can buttons at the top of the page.

5. A Bird's Eye View of Other Functions You Might Want to Explore
-----------------------------------------------------------------

When you open your breed list results file, you will notice the
following:

1) All of the rows of the output are included, even though you can only
   see 1000 of those rows when you run the query through the Jupyter
   interface.

2) There are some strange values in the breed list. Some of the entries
   in the breed column seem to have a dash included before the name.
   This is an example of what real business data sets look like...they
   are messy! We will use this as an opportunity to highlight why it is
   so important to be curious and explore MySQL functions on your own.

If you needed an accurate list of all the dog breeds in the dogs table,
you would have to find some way to "clean up" the breed list you just
made. Let's examine some of the functions that could help you achieve
this cleaning using SQL syntax rather than another program or language
outside of the database.

| I included these links to MySQL functions in an earlier notebook:
| http://dev.mysql.com/doc/refman/5.7/en/func-op-summary-ref.html
| http://www.w3resource.com/mysql/mysql-functions-and-operators.php

The following description of a function called REPLACE is included in
that resource:

| "REPLACE(str,from\_str,to\_str)
| Returns the string str with all occurrences of the string from\_str
  replaced by the string to\_str. REPLACE() performs a case-sensitive
  match when searching for from\_str."

One thing we could try is using this function to replace any dashes
included in the breed names with no character:

.. code:: mysql

    SELECT DISTINCT breed,
    REPLACE(breed,'-','') AS breed_fixed
    FROM dogs
    ORDER BY breed_fixed

In this query, we put the field/column name in the replace function
where the syntax instructions listed "str" in order to tell the REPLACE
function to act on the entire column. The "-" was the "from\_str", which
is the string we wanted to replace. The "" was the to\_str, which is the
character with which we want to replace the "from\_str".

**Try looking at the output:**

.. code:: ipython3

    %%sql
    SELECT DISTINCT breed,
    REPLACE(breed,'-','') AS breed_fixed
    FROM dogs
    ORDER BY breed_fixed;


.. parsed-literal::

    2006 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>breed</th>
            <th>breed_fixed</th>
        </tr>
        <tr>
            <td>Affenpinscher</td>
            <td>Affenpinscher</td>
        </tr>
        <tr>
            <td>Affenpinscher-Afghan Hound Mix</td>
            <td>AffenpinscherAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Airedale Terrier Mix</td>
            <td>AffenpinscherAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Alaskan Malamute Mix</td>
            <td>AffenpinscherAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-American English Coonhound Mix</td>
            <td>AffenpinscherAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Brussels Griffon Mix</td>
            <td>AffenpinscherBrussels Griffon Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Poodle Mix</td>
            <td>AffenpinscherPoodle Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Rat Terrier Mix</td>
            <td>AffenpinscherRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Spanish Water Dog Mix</td>
            <td>AffenpinscherSpanish Water Dog Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound</td>
            <td>Afghan Hound</td>
        </tr>
        <tr>
            <td>Afghan Hound-Affenpinscher Mix</td>
            <td>Afghan HoundAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Airedale Terrier Mix</td>
            <td>Afghan HoundAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Akita Mix</td>
            <td>Afghan HoundAkita Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Bloodhound Mix</td>
            <td>Afghan HoundBloodhound Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Border Collie Mix</td>
            <td>Afghan HoundBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Golden Retriever Mix</td>
            <td>Afghan HoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier</td>
            <td>Airedale Terrier</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Afghan Hound Mix</td>
            <td>Airedale TerrierAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Border Collie Mix</td>
            <td>Airedale TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Catahoula Leopard Dog Mix</td>
            <td>Airedale TerrierCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shepherd Dog Mix</td>
            <td>Airedale TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shorthaired Pointer Mix</td>
            <td>Airedale TerrierGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Golden Retriever Mix</td>
            <td>Airedale TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Labrador Retriever Mix</td>
            <td>Airedale TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Portuguese Podengo Pequeno Mix</td>
            <td>Airedale TerrierPortuguese Podengo Pequeno Mix</td>
        </tr>
        <tr>
            <td>Akita</td>
            <td>Akita</td>
        </tr>
        <tr>
            <td>Akita- Mix</td>
            <td>Akita Mix</td>
        </tr>
        <tr>
            <td>Akita-Affenpinscher Mix</td>
            <td>AkitaAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>Akita-Afghan Hound Mix</td>
            <td>AkitaAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>Akita-Airedale Terrier Mix</td>
            <td>AkitaAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-American Pit Bull Terrier Mix</td>
            <td>AkitaAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-Bearded Collie Mix</td>
            <td>AkitaBearded Collie Mix</td>
        </tr>
        <tr>
            <td>Akita-Belgian Tervuren Mix</td>
            <td>AkitaBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Akita-Bernese Mountain Dog Mix</td>
            <td>AkitaBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-German Shepherd Dog Mix</td>
            <td>AkitaGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-Labrador Retriever Mix</td>
            <td>AkitaLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Akita-Siberian Husky Mix</td>
            <td>AkitaSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute</td>
            <td>Alaskan Malamute</td>
        </tr>
        <tr>
            <td>Alaskan Malamute- Mix</td>
            <td>Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-American Pit Bull Terrier Mix</td>
            <td>Alaskan MalamuteAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Australian Kelpie Mix</td>
            <td>Alaskan MalamuteAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Beagle Mix</td>
            <td>Alaskan MalamuteBeagle Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Bernese Mountain Dog Mix</td>
            <td>Alaskan MalamuteBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Border Collie Mix</td>
            <td>Alaskan MalamuteBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Collie Mix</td>
            <td>Alaskan MalamuteCollie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-English Cocker Spaniel Mix</td>
            <td>Alaskan MalamuteEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-German Shepherd Dog Mix</td>
            <td>Alaskan MalamuteGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Labrador Retriever Mix</td>
            <td>Alaskan MalamuteLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Pomeranian Mix</td>
            <td>Alaskan MalamutePomeranian Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Siberian Husky Mix</td>
            <td>Alaskan MalamuteSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound</td>
            <td>American English Coonhound</td>
        </tr>
        <tr>
            <td>American English Coonhound-Golden Retriever Mix</td>
            <td>American English CoonhoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Redbone Coonhound Mix</td>
            <td>American English CoonhoundRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Rhodesian Ridgeback Mix</td>
            <td>American English CoonhoundRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Weimaraner Mix</td>
            <td>American English CoonhoundWeimaraner Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog</td>
            <td>American Eskimo Dog</td>
        </tr>
        <tr>
            <td>-American Eskimo Dog Mix</td>
            <td>American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog- Mix</td>
            <td>American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Australian Shepherd Mix</td>
            <td>American Eskimo DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Border Collie Mix</td>
            <td>American Eskimo DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Chihuahua Mix</td>
            <td>American Eskimo DogChihuahua Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Cocker Spaniel Mix</td>
            <td>American Eskimo DogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Collie Mix</td>
            <td>American Eskimo DogCollie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-English Springer Spaniel Mix</td>
            <td>American Eskimo DogEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Golden Retriever Mix</td>
            <td>American Eskimo DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Papillon Mix</td>
            <td>American Eskimo DogPapillon Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pembroke Welsh Corgi Mix</td>
            <td>American Eskimo DogPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pomeranian Mix</td>
            <td>American Eskimo DogPomeranian Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Poodle Mix</td>
            <td>American Eskimo DogPoodle Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Russell Terrier Mix</td>
            <td>American Eskimo DogRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Shiba Inu Mix</td>
            <td>American Eskimo DogShiba Inu Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Siberian Husky Mix</td>
            <td>American Eskimo DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Staffordshire Bull Terrier Mix</td>
            <td>American Eskimo DogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Foxhound</td>
            <td>American Foxhound</td>
        </tr>
        <tr>
            <td>American Foxhound- Mix</td>
            <td>American Foxhound Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Anatolian Shepherd Dog Mix</td>
            <td>American FoxhoundAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Beagle Mix</td>
            <td>American FoxhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-German Shepherd Dog Mix</td>
            <td>American FoxhoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Labrador Retriever Mix</td>
            <td>American FoxhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Pointer Mix</td>
            <td>American FoxhoundPointer Mix</td>
        </tr>
        <tr>
            <td>American Hairless Terrier</td>
            <td>American Hairless Terrier</td>
        </tr>
        <tr>
            <td>American Hairless Terrier-Shetland Sheepdog Mix</td>
            <td>American Hairless TerrierShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>American Leopard Hound</td>
            <td>American Leopard Hound</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier</td>
            <td>American Pit Bull Terrier</td>
        </tr>
        <tr>
            <td>-American Pit Bull Terrier Mix</td>
            <td>American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier- Mix</td>
            <td>American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American English Coonhound Mix</td>
            <td>American Pit Bull TerrierAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Leopard Hound Mix</td>
            <td>American Pit Bull TerrierAmerican Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Staffordshire Terrier Mix</td>
            <td>American Pit Bull TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Cattle Dog Mix</td>
            <td>American Pit Bull TerrierAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Shepherd Mix</td>
            <td>American Pit Bull TerrierAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Beagle Mix</td>
            <td>American Pit Bull TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Border Collie Mix</td>
            <td>American Pit Bull TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boston Terrier Mix</td>
            <td>American Pit Bull TerrierBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boxer Mix</td>
            <td>American Pit Bull TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Brittany Mix</td>
            <td>American Pit Bull TerrierBrittany Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bull Terrier Mix</td>
            <td>American Pit Bull TerrierBull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bulldog Mix</td>
            <td>American Pit Bull TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bullmastiff Mix</td>
            <td>American Pit Bull TerrierBullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cane Corso Mix</td>
            <td>American Pit Bull TerrierCane Corso Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cardigan Welsh Corgi Mix</td>
            <td>American Pit Bull TerrierCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Chinese Shar-Pei Mix</td>
            <td>American Pit Bull TerrierChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Doberman Pinscher Mix</td>
            <td>American Pit Bull TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Dogue de Bordeaux Mix</td>
            <td>American Pit Bull TerrierDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-German Shepherd Dog Mix</td>
            <td>American Pit Bull TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Dane Mix</td>
            <td>American Pit Bull TerrierGreat Dane Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Pyrenees Mix</td>
            <td>American Pit Bull TerrierGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Greyhound Mix</td>
            <td>American Pit Bull TerrierGreyhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Labrador Retriever Mix</td>
            <td>American Pit Bull TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Mastiff Mix</td>
            <td>American Pit Bull TerrierMastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Parson Russell Terrier Mix</td>
            <td>American Pit Bull TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Plott Mix</td>
            <td>American Pit Bull TerrierPlott Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Pointer Mix</td>
            <td>American Pit Bull TerrierPointer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rhodesian Ridgeback Mix</td>
            <td>American Pit Bull TerrierRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rottweiler Mix</td>
            <td>American Pit Bull TerrierRottweiler Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Siberian Husky Mix</td>
            <td>American Pit Bull TerrierSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Staffordshire Bull Terrier Mix</td>
            <td>American Pit Bull TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Treeing Tennessee Brindle Mix</td>
            <td>American Pit Bull TerrierTreeing Tennessee Brindle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Vizsla Mix</td>
            <td>American Pit Bull TerrierVizsla Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Whippet Mix</td>
            <td>American Pit Bull TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier</td>
            <td>American Staffordshire Terrier</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier- Mix</td>
            <td>American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Airedale Terrier Mix</td>
            <td>American Staffordshire TerrierAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-American Pit Bull Terrier Mix</td>
            <td>American Staffordshire TerrierAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Australian Shepherd Mix</td>
            <td>American Staffordshire TerrierAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Beagle Mix</td>
            <td>American Staffordshire TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Border Collie Mix</td>
            <td>American Staffordshire TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boston Terrier Mix</td>
            <td>American Staffordshire TerrierBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boxer Mix</td>
            <td>American Staffordshire TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bull Terrier Mix</td>
            <td>American Staffordshire TerrierBull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bulldog Mix</td>
            <td>American Staffordshire TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bullmastiff Mix</td>
            <td>American Staffordshire TerrierBullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Catahoula Leopard Dog Mix</td>
            <td>American Staffordshire TerrierCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chinese Shar-Pei Mix</td>
            <td>American Staffordshire TerrierChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chow Chow Mix</td>
            <td>American Staffordshire TerrierChow Chow Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dalmatian Mix</td>
            <td>American Staffordshire TerrierDalmatian Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Doberman Pinscher Mix</td>
            <td>American Staffordshire TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogo Argentino Mix</td>
            <td>American Staffordshire TerrierDogo Argentino Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogue de Bordeaux Mix</td>
            <td>American Staffordshire TerrierDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Shepherd Dog Mix</td>
            <td>American Staffordshire TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Wirehaired Pointer Mix</td>
            <td>American Staffordshire TerrierGerman Wirehaired Pointer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Golden Retriever Mix</td>
            <td>American Staffordshire TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Gordon Setter Mix</td>
            <td>American Staffordshire TerrierGordon Setter Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Dane Mix</td>
            <td>American Staffordshire TerrierGreat Dane Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Pyrenees Mix</td>
            <td>American Staffordshire TerrierGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Greyhound Mix</td>
            <td>American Staffordshire TerrierGreyhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Labrador Retriever Mix</td>
            <td>American Staffordshire TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Lancashire Heeler Mix</td>
            <td>American Staffordshire TerrierLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Mastiff Mix</td>
            <td>American Staffordshire TerrierMastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Miniature Bull Terrier Mix</td>
            <td>American Staffordshire TerrierMiniature Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Neapolitan Mastiff Mix</td>
            <td>American Staffordshire TerrierNeapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Portuguese Podengo Mix</td>
            <td>American Staffordshire TerrierPortuguese Podengo Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Redbone Coonhound Mix</td>
            <td>American Staffordshire TerrierRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Rhodesian Ridgeback Mix</td>
            <td>American Staffordshire TerrierRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Staffordshire Bull Terrier Mix</td>
            <td>American Staffordshire TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Treeing Walker Coonhound Mix</td>
            <td>American Staffordshire TerrierTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Weimaraner Mix</td>
            <td>American Staffordshire TerrierWeimaraner Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Whippet Mix</td>
            <td>American Staffordshire TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>American Water Spaniel</td>
            <td>American Water Spaniel</td>
        </tr>
        <tr>
            <td>American Water Spaniel-Dachshund Mix</td>
            <td>American Water SpanielDachshund Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog</td>
            <td>Anatolian Shepherd Dog</td>
        </tr>
        <tr>
            <td>-Anatolian Shepherd Dog Mix</td>
            <td>Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Border Collie Mix</td>
            <td>Anatolian Shepherd DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Great Pyrenees Mix</td>
            <td>Anatolian Shepherd DogGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Labrador Retriever Mix</td>
            <td>Anatolian Shepherd DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Mastiff Mix</td>
            <td>Anatolian Shepherd DogMastiff Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde</td>
            <td>Appenzeller Sennenhunde</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde- Mix</td>
            <td>Appenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Border Collie Mix</td>
            <td>Appenzeller SennenhundeBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Collie Mix</td>
            <td>Appenzeller SennenhundeCollie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog</td>
            <td>Australian Cattle Dog</td>
        </tr>
        <tr>
            <td>-Australian Cattle Dog Mix</td>
            <td>Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog- Mix</td>
            <td>Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Pit Bull Terrier Mix</td>
            <td>Australian Cattle DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Staffordshire Terrier Mix</td>
            <td>Australian Cattle DogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Anatolian Shepherd Dog Mix</td>
            <td>Australian Cattle DogAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Kelpie Mix</td>
            <td>Australian Cattle DogAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Shepherd Mix</td>
            <td>Australian Cattle DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Basenji Mix</td>
            <td>Australian Cattle DogBasenji Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Beagle Mix</td>
            <td>Australian Cattle DogBeagle Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bearded Collie Mix</td>
            <td>Australian Cattle DogBearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Belgian Sheepdog Mix</td>
            <td>Australian Cattle DogBelgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bernese Mountain Dog Mix</td>
            <td>Australian Cattle DogBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bluetick Coonhound Mix</td>
            <td>Australian Cattle DogBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Border Collie Mix</td>
            <td>Australian Cattle DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Boxer Mix</td>
            <td>Australian Cattle DogBoxer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bull Terrier Mix</td>
            <td>Australian Cattle DogBull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cardigan Welsh Corgi Mix</td>
            <td>Australian Cattle DogCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Catahoula Leopard Dog Mix</td>
            <td>Australian Cattle DogCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Chow Chow Mix</td>
            <td>Australian Cattle DogChow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cocker Spaniel Mix</td>
            <td>Australian Cattle DogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Curly-Coated Retriever Mix</td>
            <td>Australian Cattle DogCurlyCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Doberman Pinscher Mix</td>
            <td>Australian Cattle DogDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Longhaired Pointer Mix</td>
            <td>Australian Cattle DogGerman Longhaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Shepherd Dog Mix</td>
            <td>Australian Cattle DogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Greyhound Mix</td>
            <td>Australian Cattle DogGreyhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Labrador Retriever Mix</td>
            <td>Australian Cattle DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rat Terrier Mix</td>
            <td>Australian Cattle DogRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Redbone Coonhound Mix</td>
            <td>Australian Cattle DogRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rottweiler Mix</td>
            <td>Australian Cattle DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Shetland Sheepdog Mix</td>
            <td>Australian Cattle DogShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Siberian Husky Mix</td>
            <td>Australian Cattle DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Staffordshire Bull Terrier Mix</td>
            <td>Australian Cattle DogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Treeing Walker Coonhound Mix</td>
            <td>Australian Cattle DogTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Weimaraner Mix</td>
            <td>Australian Cattle DogWeimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie</td>
            <td>Australian Kelpie</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Australian Cattle Dog Mix</td>
            <td>Australian KelpieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Basenji Mix</td>
            <td>Australian KelpieBasenji Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Border Collie Mix</td>
            <td>Australian KelpieBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Labrador Retriever Mix</td>
            <td>Australian KelpieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Miniature Schnauzer Mix</td>
            <td>Australian KelpieMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Rottweiler Mix</td>
            <td>Australian KelpieRottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Staffordshire Bull Terrier Mix</td>
            <td>Australian KelpieStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Labradoodle</td>
            <td>Australian Labradoodle</td>
        </tr>
        <tr>
            <td>Australian Labradoodle-Poodle Mix</td>
            <td>Australian LabradoodlePoodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd</td>
            <td>Australian Shepherd</td>
        </tr>
        <tr>
            <td>-Australian Shepherd Mix</td>
            <td>Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd- Mix</td>
            <td>Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Alaskan Malamute Mix</td>
            <td>Australian ShepherdAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-American Pit Bull Terrier Mix</td>
            <td>Australian ShepherdAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Australian Cattle Dog Mix</td>
            <td>Australian ShepherdAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Basenji Mix</td>
            <td>Australian ShepherdBasenji Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Beagle Mix</td>
            <td>Australian ShepherdBeagle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bearded Collie Mix</td>
            <td>Australian ShepherdBearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bloodhound Mix</td>
            <td>Australian ShepherdBloodhound Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Border Collie Mix</td>
            <td>Australian ShepherdBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cardigan Welsh Corgi Mix</td>
            <td>Australian ShepherdCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Catahoula Leopard Dog Mix</td>
            <td>Australian ShepherdCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Chow Chow Mix</td>
            <td>Australian ShepherdChow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cocker Spaniel Mix</td>
            <td>Australian ShepherdCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Collie Mix</td>
            <td>Australian ShepherdCollie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Doberman Pinscher Mix</td>
            <td>Australian ShepherdDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-English Cocker Spaniel Mix</td>
            <td>Australian ShepherdEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Flat-Coated Retriever Mix</td>
            <td>Australian ShepherdFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-German Shepherd Dog Mix</td>
            <td>Australian ShepherdGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Golden Retriever Mix</td>
            <td>Australian ShepherdGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Great Pyrenees Mix</td>
            <td>Australian ShepherdGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Labrador Retriever Mix</td>
            <td>Australian ShepherdLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pembroke Welsh Corgi Mix</td>
            <td>Australian ShepherdPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Poodle Mix</td>
            <td>Australian ShepherdPoodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pug Mix</td>
            <td>Australian ShepherdPug Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rhodesian Ridgeback Mix</td>
            <td>Australian ShepherdRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rottweiler Mix</td>
            <td>Australian ShepherdRottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Schipperke Mix</td>
            <td>Australian ShepherdSchipperke Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shetland Sheepdog Mix</td>
            <td>Australian ShepherdShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shiba Inu Mix</td>
            <td>Australian ShepherdShiba Inu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shih Tzu Mix</td>
            <td>Australian ShepherdShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Siberian Husky Mix</td>
            <td>Australian ShepherdSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-St. Bernard Mix</td>
            <td>Australian ShepherdSt. Bernard Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Standard Poodle Mix</td>
            <td>Australian ShepherdStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Weimaraner Mix</td>
            <td>Australian ShepherdWeimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier</td>
            <td>Australian Terrier</td>
        </tr>
        <tr>
            <td>Australian Terrier-Lowchen Mix</td>
            <td>Australian TerrierLowchen Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Parson Russell Terrier Mix</td>
            <td>Australian TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Rottweiler Mix</td>
            <td>Australian TerrierRottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Yorkshire Terrier Mix</td>
            <td>Australian TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Barbet</td>
            <td>Barbet</td>
        </tr>
        <tr>
            <td>Basenji</td>
            <td>Basenji</td>
        </tr>
        <tr>
            <td>Basenji- Mix</td>
            <td>Basenji Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Staffordshire Terrier Mix</td>
            <td>BasenjiAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Water Spaniel Mix</td>
            <td>BasenjiAmerican Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-Australian Cattle Dog Mix</td>
            <td>BasenjiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-Beagle Mix</td>
            <td>BasenjiBeagle Mix</td>
        </tr>
        <tr>
            <td>Basenji-Cardigan Welsh Corgi Mix</td>
            <td>BasenjiCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basenji-English Springer Spaniel Mix</td>
            <td>BasenjiEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shepherd Dog Mix</td>
            <td>BasenjiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shorthaired Pointer Mix</td>
            <td>BasenjiGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Basenji-Manchester Terrier Mix</td>
            <td>BasenjiManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Russell Terrier Mix</td>
            <td>BasenjiRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Shiba Inu Mix</td>
            <td>BasenjiShiba Inu Mix</td>
        </tr>
        <tr>
            <td>Basenji-Siberian Husky Mix</td>
            <td>BasenjiSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Basenji-Whippet Mix</td>
            <td>BasenjiWhippet Mix</td>
        </tr>
        <tr>
            <td>Basset Hound</td>
            <td>Basset Hound</td>
        </tr>
        <tr>
            <td>Basset Hound- Mix</td>
            <td>Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Airedale Terrier Mix</td>
            <td>Basset HoundAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American English Coonhound Mix</td>
            <td>Basset HoundAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Pit Bull Terrier Mix</td>
            <td>Basset HoundAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Staffordshire Terrier Mix</td>
            <td>Basset HoundAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Cattle Dog Mix</td>
            <td>Basset HoundAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Shepherd Mix</td>
            <td>Basset HoundAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Beagle Mix</td>
            <td>Basset HoundBeagle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Boston Terrier Mix</td>
            <td>Basset HoundBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cardigan Welsh Corgi Mix</td>
            <td>Basset HoundCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cocker Spaniel Mix</td>
            <td>Basset HoundCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Dachshund Mix</td>
            <td>Basset HoundDachshund Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-German Shepherd Dog Mix</td>
            <td>Basset HoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Great Pyrenees Mix</td>
            <td>Basset HoundGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Labrador Retriever Mix</td>
            <td>Basset HoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pembroke Welsh Corgi Mix</td>
            <td>Basset HoundPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pointer Mix</td>
            <td>Basset HoundPointer Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Poodle Mix</td>
            <td>Basset HoundPoodle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Rottweiler Mix</td>
            <td>Basset HoundRottweiler Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Russell Terrier Mix</td>
            <td>Basset HoundRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Staffordshire Bull Terrier Mix</td>
            <td>Basset HoundStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle</td>
            <td>Beagle</td>
        </tr>
        <tr>
            <td>-Beagle Mix</td>
            <td>Beagle Mix</td>
        </tr>
        <tr>
            <td>Beagle- Mix</td>
            <td>Beagle Mix</td>
        </tr>
        <tr>
            <td>Beagle-American English Coonhound Mix</td>
            <td>BeagleAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Eskimo Dog Mix</td>
            <td>BeagleAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Foxhound Mix</td>
            <td>BeagleAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Australian Cattle Dog Mix</td>
            <td>BeagleAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Basset Hound Mix</td>
            <td>BeagleBasset Hound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bluetick Coonhound Mix</td>
            <td>BeagleBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Collie Mix</td>
            <td>BeagleBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Terrier Mix</td>
            <td>BeagleBorder Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boston Terrier Mix</td>
            <td>BeagleBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boxer Mix</td>
            <td>BeagleBoxer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bulldog Mix</td>
            <td>BeagleBulldog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cavalier King Charles Spaniel Mix</td>
            <td>BeagleCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chihuahua Mix</td>
            <td>BeagleChihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chinese Shar-Pei Mix</td>
            <td>BeagleChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chow Chow Mix</td>
            <td>BeagleChow Chow Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cocker Spaniel Mix</td>
            <td>BeagleCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Collie Mix</td>
            <td>BeagleCollie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Dachshund Mix</td>
            <td>BeagleDachshund Mix</td>
        </tr>
        <tr>
            <td>Beagle-German Shepherd Dog Mix</td>
            <td>BeagleGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Golden Retriever Mix</td>
            <td>BeagleGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Greyhound Mix</td>
            <td>BeagleGreyhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Jack Russell Terrier Mix</td>
            <td>BeagleJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Labrador Retriever Mix</td>
            <td>BeagleLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Miniature Schnauzer Mix</td>
            <td>BeagleMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Parson Russell Terrier Mix</td>
            <td>BeagleParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pekingese Mix</td>
            <td>BeaglePekingese Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pointer Mix</td>
            <td>BeaglePointer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Poodle Mix</td>
            <td>BeaglePoodle Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pug Mix</td>
            <td>BeaglePug Mix</td>
        </tr>
        <tr>
            <td>Beagle-Rat Terrier Mix</td>
            <td>BeagleRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Russell Terrier Mix</td>
            <td>BeagleRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Schipperke Mix</td>
            <td>BeagleSchipperke Mix</td>
        </tr>
        <tr>
            <td>Beagle-Shetland Sheepdog Mix</td>
            <td>BeagleShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Siberian Husky Mix</td>
            <td>BeagleSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Beagle-Smooth Fox Terrier Mix</td>
            <td>BeagleSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Toy Fox Terrier Mix</td>
            <td>BeagleToy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Treeing Walker Coonhound Mix</td>
            <td>BeagleTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Whippet Mix</td>
            <td>BeagleWhippet Mix</td>
        </tr>
        <tr>
            <td>Beaglier</td>
            <td>Beaglier</td>
        </tr>
        <tr>
            <td>Bearded Collie</td>
            <td>Bearded Collie</td>
        </tr>
        <tr>
            <td>Bearded Collie-Beagle Mix</td>
            <td>Bearded CollieBeagle Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Bernese Mountain Dog Mix</td>
            <td>Bearded CollieBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Border Collie Mix</td>
            <td>Bearded CollieBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Labrador Retriever Mix</td>
            <td>Bearded CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Shih Tzu Mix</td>
            <td>Bearded CollieShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Soft Coated Wheaten Terrier Mix</td>
            <td>Bearded CollieSoft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Tibetan Terrier Mix</td>
            <td>Bearded CollieTibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Beauceron</td>
            <td>Beauceron</td>
        </tr>
        <tr>
            <td>Beauceron-Rottweiler Mix</td>
            <td>BeauceronRottweiler Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier</td>
            <td>Bedlington Terrier</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Belgian Laekenois Mix</td>
            <td>Bedlington TerrierBelgian Laekenois Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Whippet Mix</td>
            <td>Bedlington TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>Belgian Laekenois</td>
            <td>Belgian Laekenois</td>
        </tr>
        <tr>
            <td>Belgian Malinois</td>
            <td>Belgian Malinois</td>
        </tr>
        <tr>
            <td>Belgian Malinois- Mix</td>
            <td>Belgian Malinois Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-American Staffordshire Terrier Mix</td>
            <td>Belgian MalinoisAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Belgian Tervuren Mix</td>
            <td>Belgian MalinoisBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Border Collie Mix</td>
            <td>Belgian MalinoisBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chinese Shar-Pei Mix</td>
            <td>Belgian MalinoisChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chow Chow Mix</td>
            <td>Belgian MalinoisChow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Dutch Shepherd Mix</td>
            <td>Belgian MalinoisDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-German Shepherd Dog Mix</td>
            <td>Belgian MalinoisGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Labrador Retriever Mix</td>
            <td>Belgian MalinoisLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Siberian Husky Mix</td>
            <td>Belgian MalinoisSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog</td>
            <td>Belgian Sheepdog</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog- Mix</td>
            <td>Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Border Collie Mix</td>
            <td>Belgian SheepdogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Chow Chow Mix</td>
            <td>Belgian SheepdogChow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Dutch Shepherd Mix</td>
            <td>Belgian SheepdogDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-German Shepherd Dog Mix</td>
            <td>Belgian SheepdogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Golden Retriever Mix</td>
            <td>Belgian SheepdogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Lhasa Apso Mix</td>
            <td>Belgian SheepdogLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren</td>
            <td>Belgian Tervuren</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Basenji Mix</td>
            <td>Belgian TervurenBasenji Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Border Collie Mix</td>
            <td>Belgian TervurenBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Boston Terrier Mix</td>
            <td>Belgian TervurenBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Whippet Mix</td>
            <td>Belgian TervurenWhippet Mix</td>
        </tr>
        <tr>
            <td>Bergamasco-Old English Sheepdog Mix</td>
            <td>BergamascoOld English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Berger Picard</td>
            <td>Berger Picard</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog</td>
            <td>Bernese Mountain Dog</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Border Collie Mix</td>
            <td>Bernese Mountain DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Chow Chow Mix</td>
            <td>Bernese Mountain DogChow Chow Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-English Springer Spaniel Mix</td>
            <td>Bernese Mountain DogEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Golden Retriever Mix</td>
            <td>Bernese Mountain DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Great Pyrenees Mix</td>
            <td>Bernese Mountain DogGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Greater Swiss Mountain Dog Mix</td>
            <td>Bernese Mountain DogGreater Swiss Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Labrador Retriever Mix</td>
            <td>Bernese Mountain DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Poodle Mix</td>
            <td>Bernese Mountain DogPoodle Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Rottweiler Mix</td>
            <td>Bernese Mountain DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Standard Poodle Mix</td>
            <td>Bernese Mountain DogStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise</td>
            <td>Bichon Frise</td>
        </tr>
        <tr>
            <td>-Bichon Frise Mix</td>
            <td>Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise- Mix</td>
            <td>Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-American Eskimo Dog Mix</td>
            <td>Bichon FriseAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cavalier King Charles Spaniel Mix</td>
            <td>Bichon FriseCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Chinese Crested Mix</td>
            <td>Bichon FriseChinese Crested Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cocker Spaniel Mix</td>
            <td>Bichon FriseCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Golden Retriever Mix</td>
            <td>Bichon FriseGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Havanese Mix</td>
            <td>Bichon FriseHavanese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Jack Russell Terrier Mix</td>
            <td>Bichon FriseJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Lhasa Apso Mix</td>
            <td>Bichon FriseLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Maltese Mix</td>
            <td>Bichon FriseMaltese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Miniature Schnauzer Mix</td>
            <td>Bichon FriseMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Pomeranian Mix</td>
            <td>Bichon FrisePomeranian Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Poodle Mix</td>
            <td>Bichon FrisePoodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Shih Tzu Mix</td>
            <td>Bichon FriseShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-West Highland White Terrier Mix</td>
            <td>Bichon FriseWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Yorkshire Terrier Mix</td>
            <td>Bichon FriseYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound</td>
            <td>Black and Tan Coonhound</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound- Mix</td>
            <td>Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Beagle Mix</td>
            <td>Black and Tan CoonhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-German Shepherd Dog Mix</td>
            <td>Black and Tan CoonhoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Golden Retriever Mix</td>
            <td>Black and Tan CoonhoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Labrador Retriever Mix</td>
            <td>Black and Tan CoonhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Plott Mix</td>
            <td>Black and Tan CoonhoundPlott Mix</td>
        </tr>
        <tr>
            <td>Black Russian Terrier</td>
            <td>Black Russian Terrier</td>
        </tr>
        <tr>
            <td>Bloodhound</td>
            <td>Bloodhound</td>
        </tr>
        <tr>
            <td>Bloodhound-Beagle Mix</td>
            <td>BloodhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Black and Tan Coonhound Mix</td>
            <td>BloodhoundBlack and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Bull Terrier Mix</td>
            <td>BloodhoundBull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Irish Setter Mix</td>
            <td>BloodhoundIrish Setter Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Labrador Retriever Mix</td>
            <td>BloodhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound</td>
            <td>Bluetick Coonhound</td>
        </tr>
        <tr>
            <td>-Bluetick Coonhound Mix</td>
            <td>Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Beagle Mix</td>
            <td>Bluetick CoonhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-German Shorthaired Pointer Mix</td>
            <td>Bluetick CoonhoundGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Jack Russell Terrier Mix</td>
            <td>Bluetick CoonhoundJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Pointer Mix</td>
            <td>Bluetick CoonhoundPointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Rottweiler Mix</td>
            <td>Bluetick CoonhoundRottweiler Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Treeing Walker Coonhound Mix</td>
            <td>Bluetick CoonhoundTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boerboel</td>
            <td>Boerboel</td>
        </tr>
        <tr>
            <td>Bolognese</td>
            <td>Bolognese</td>
        </tr>
        <tr>
            <td>Border Collie</td>
            <td>Border Collie</td>
        </tr>
        <tr>
            <td>-Border Collie Mix</td>
            <td>Border Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie- Mix</td>
            <td>Border Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Affenpinscher Mix</td>
            <td>Border CollieAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Akita Mix</td>
            <td>Border CollieAkita Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Eskimo Dog Mix</td>
            <td>Border CollieAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Foxhound Mix</td>
            <td>Border CollieAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Pit Bull Terrier Mix</td>
            <td>Border CollieAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Staffordshire Terrier Mix</td>
            <td>Border CollieAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Cattle Dog Mix</td>
            <td>Border CollieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Kelpie Mix</td>
            <td>Border CollieAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Shepherd Mix</td>
            <td>Border CollieAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beagle Mix</td>
            <td>Border CollieBeagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bearded Collie Mix</td>
            <td>Border CollieBearded Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beauceron Mix</td>
            <td>Border CollieBeauceron Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Sheepdog Mix</td>
            <td>Border CollieBelgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Tervuren Mix</td>
            <td>Border CollieBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bernese Mountain Dog Mix</td>
            <td>Border CollieBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bloodhound Mix</td>
            <td>Border CollieBloodhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bluetick Coonhound Mix</td>
            <td>Border CollieBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Borzoi Mix</td>
            <td>Border CollieBorzoi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Boxer Mix</td>
            <td>Border CollieBoxer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Brittany Mix</td>
            <td>Border CollieBrittany Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bull Terrier Mix</td>
            <td>Border CollieBull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cavalier King Charles Spaniel Mix</td>
            <td>Border CollieCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Chow Chow Mix</td>
            <td>Border CollieChow Chow Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cocker Spaniel Mix</td>
            <td>Border CollieCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Collie Mix</td>
            <td>Border CollieCollie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Dalmatian Mix</td>
            <td>Border CollieDalmatian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Cocker Spaniel Mix</td>
            <td>Border CollieEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Setter Mix</td>
            <td>Border CollieEnglish Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Springer Spaniel Mix</td>
            <td>Border CollieEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Field Spaniel Mix</td>
            <td>Border CollieField Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Flat-Coated Retriever Mix</td>
            <td>Border CollieFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shepherd Dog Mix</td>
            <td>Border CollieGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shorthaired Pointer Mix</td>
            <td>Border CollieGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Golden Retriever Mix</td>
            <td>Border CollieGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Dane Mix</td>
            <td>Border CollieGreat Dane Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Pyrenees Mix</td>
            <td>Border CollieGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Greyhound Mix</td>
            <td>Border CollieGreyhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Icelandic Sheepdog Mix</td>
            <td>Border CollieIcelandic Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Setter Mix</td>
            <td>Border CollieIrish Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Water Spaniel Mix</td>
            <td>Border CollieIrish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Jack Russell Terrier Mix</td>
            <td>Border CollieJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Keeshond Mix</td>
            <td>Border CollieKeeshond Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Kooikerhondje Mix</td>
            <td>Border CollieKooikerhondje Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Labrador Retriever Mix</td>
            <td>Border CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Lancashire Heeler Mix</td>
            <td>Border CollieLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Australian Shepherd Mix</td>
            <td>Border CollieMiniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Pinscher Mix</td>
            <td>Border CollieMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Newfoundland Mix</td>
            <td>Border CollieNewfoundland Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Parson Russell Terrier Mix</td>
            <td>Border CollieParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pembroke Welsh Corgi Mix</td>
            <td>Border ColliePembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pointer Mix</td>
            <td>Border ColliePointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pomeranian Mix</td>
            <td>Border ColliePomeranian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Poodle Mix</td>
            <td>Border ColliePoodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rhodesian Ridgeback Mix</td>
            <td>Border CollieRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rottweiler Mix</td>
            <td>Border CollieRottweiler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Saluki Mix</td>
            <td>Border CollieSaluki Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Shetland Sheepdog Mix</td>
            <td>Border CollieShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Siberian Husky Mix</td>
            <td>Border CollieSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Soft Coated Wheaten Terrier Mix</td>
            <td>Border CollieSoft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Staffordshire Bull Terrier Mix</td>
            <td>Border CollieStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Poodle Mix</td>
            <td>Border CollieStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Schnauzer Mix</td>
            <td>Border CollieStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Welsh Springer Spaniel Mix</td>
            <td>Border CollieWelsh Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-West Highland White Terrier Mix</td>
            <td>Border CollieWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Whippet Mix</td>
            <td>Border CollieWhippet Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Wire Fox Terrier Mix</td>
            <td>Border CollieWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier</td>
            <td>Border Terrier</td>
        </tr>
        <tr>
            <td>Border Terrier- Mix</td>
            <td>Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Beagle Mix</td>
            <td>Border TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Bernese Mountain Dog Mix</td>
            <td>Border TerrierBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Cairn Terrier Mix</td>
            <td>Border TerrierCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Dachshund Mix</td>
            <td>Border TerrierDachshund Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-English Cocker Spaniel Mix</td>
            <td>Border TerrierEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Golden Retriever Mix</td>
            <td>Border TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Lakeland Terrier Mix</td>
            <td>Border TerrierLakeland Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Parson Russell Terrier Mix</td>
            <td>Border TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Poodle Mix</td>
            <td>Border TerrierPoodle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Pug Mix</td>
            <td>Border TerrierPug Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Russell Terrier Mix</td>
            <td>Border TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Shih Tzu Mix</td>
            <td>Border TerrierShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Staffordshire Bull Terrier Mix</td>
            <td>Border TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Standard Schnauzer Mix</td>
            <td>Border TerrierStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-West Highland White Terrier Mix</td>
            <td>Border TerrierWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Borzoi</td>
            <td>Borzoi</td>
        </tr>
        <tr>
            <td>Borzoi-Whippet Mix</td>
            <td>BorzoiWhippet Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier</td>
            <td>Boston Terrier</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Pit Bull Terrier Mix</td>
            <td>Boston TerrierAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Staffordshire Terrier Mix</td>
            <td>Boston TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Beagle Mix</td>
            <td>Boston TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Bulldog Mix</td>
            <td>Boston TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Chihuahua Mix</td>
            <td>Boston TerrierChihuahua Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Dachshund Mix</td>
            <td>Boston TerrierDachshund Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Danish-Swedish Farmdog Mix</td>
            <td>Boston TerrierDanishSwedish Farmdog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Doberman Pinscher Mix</td>
            <td>Boston TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-French Bulldog Mix</td>
            <td>Boston TerrierFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Labrador Retriever Mix</td>
            <td>Boston TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pomeranian Mix</td>
            <td>Boston TerrierPomeranian Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pug Mix</td>
            <td>Boston TerrierPug Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Rat Terrier Mix</td>
            <td>Boston TerrierRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Russell Terrier Mix</td>
            <td>Boston TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres</td>
            <td>Bouvier des Flandres</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Airedale Terrier Mix</td>
            <td>Bouvier des FlandresAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Standard Poodle Mix</td>
            <td>Bouvier des FlandresStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>Boxer</td>
            <td>Boxer</td>
        </tr>
        <tr>
            <td>-Boxer Mix</td>
            <td>Boxer Mix</td>
        </tr>
        <tr>
            <td>Boxer- Mix</td>
            <td>Boxer Mix</td>
        </tr>
        <tr>
            <td>Boxer-Akita Mix</td>
            <td>BoxerAkita Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Foxhound Mix</td>
            <td>BoxerAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Pit Bull Terrier Mix</td>
            <td>BoxerAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Staffordshire Terrier Mix</td>
            <td>BoxerAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Cattle Dog Mix</td>
            <td>BoxerAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Shepherd Mix</td>
            <td>BoxerAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bloodhound Mix</td>
            <td>BoxerBloodhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Border Collie Mix</td>
            <td>BoxerBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Boxer-Boston Terrier Mix</td>
            <td>BoxerBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bull Terrier Mix</td>
            <td>BoxerBull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bulldog Mix</td>
            <td>BoxerBulldog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bullmastiff Mix</td>
            <td>BoxerBullmastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Cocker Spaniel Mix</td>
            <td>BoxerCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dachshund Mix</td>
            <td>BoxerDachshund Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dalmatian Mix</td>
            <td>BoxerDalmatian Mix</td>
        </tr>
        <tr>
            <td>Boxer-Doberman Pinscher Mix</td>
            <td>BoxerDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dutch Shepherd Mix</td>
            <td>BoxerDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Foxhound Mix</td>
            <td>BoxerEnglish Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Springer Spaniel Mix</td>
            <td>BoxerEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-German Shepherd Dog Mix</td>
            <td>BoxerGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Golden Retriever Mix</td>
            <td>BoxerGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Dane Mix</td>
            <td>BoxerGreat Dane Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Pyrenees Mix</td>
            <td>BoxerGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Boxer-Greyhound Mix</td>
            <td>BoxerGreyhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Ibizan Hound Mix</td>
            <td>BoxerIbizan Hound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Jindo Mix</td>
            <td>BoxerJindo Mix</td>
        </tr>
        <tr>
            <td>Boxer-Labrador Retriever Mix</td>
            <td>BoxerLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Manchester Terrier Mix</td>
            <td>BoxerManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Mastiff Mix</td>
            <td>BoxerMastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Poodle Mix</td>
            <td>BoxerPoodle Mix</td>
        </tr>
        <tr>
            <td>Boxer-Pug Mix</td>
            <td>BoxerPug Mix</td>
        </tr>
        <tr>
            <td>Boxer-Redbone Coonhound Mix</td>
            <td>BoxerRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rhodesian Ridgeback Mix</td>
            <td>BoxerRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rottweiler Mix</td>
            <td>BoxerRottweiler Mix</td>
        </tr>
        <tr>
            <td>Boxer-Russell Terrier Mix</td>
            <td>BoxerRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Siberian Husky Mix</td>
            <td>BoxerSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Boxer-St. Bernard Mix</td>
            <td>BoxerSt. Bernard Mix</td>
        </tr>
        <tr>
            <td>Boxer-Staffordshire Bull Terrier Mix</td>
            <td>BoxerStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Treeing Walker Coonhound Mix</td>
            <td>BoxerTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Vizsla Mix</td>
            <td>BoxerVizsla Mix</td>
        </tr>
        <tr>
            <td>Boxer-Weimaraner Mix</td>
            <td>BoxerWeimaraner Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel</td>
            <td>Boykin Spaniel</td>
        </tr>
        <tr>
            <td>Boykin Spaniel- Mix</td>
            <td>Boykin Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Deutscher Wachtelhund Mix</td>
            <td>Boykin SpanielDeutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-English Cocker Spaniel Mix</td>
            <td>Boykin SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Irish Setter Mix</td>
            <td>Boykin SpanielIrish Setter Mix</td>
        </tr>
        <tr>
            <td>Braque du Bourbonnais</td>
            <td>Braque du Bourbonnais</td>
        </tr>
        <tr>
            <td>Briard</td>
            <td>Briard</td>
        </tr>
        <tr>
            <td>Brittany</td>
            <td>Brittany</td>
        </tr>
        <tr>
            <td>Brittany-Basset Hound Mix</td>
            <td>BrittanyBasset Hound Mix</td>
        </tr>
        <tr>
            <td>Brittany-Border Collie Mix</td>
            <td>BrittanyBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Brittany-English Springer Spaniel Mix</td>
            <td>BrittanyEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shepherd Dog Mix</td>
            <td>BrittanyGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shorthaired Pointer Mix</td>
            <td>BrittanyGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Golden Retriever Mix</td>
            <td>BrittanyGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Irish Setter Mix</td>
            <td>BrittanyIrish Setter Mix</td>
        </tr>
        <tr>
            <td>Brittany-Labrador Retriever Mix</td>
            <td>BrittanyLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pekingese Mix</td>
            <td>BrittanyPekingese Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pointer Mix</td>
            <td>BrittanyPointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Poodle Mix</td>
            <td>BrittanyPoodle Mix</td>
        </tr>
        <tr>
            <td>Brittany-Siberian Husky Mix</td>
            <td>BrittanySiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon</td>
            <td>Brussels Griffon</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Border Terrier Mix</td>
            <td>Brussels GriffonBorder Terrier Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Poodle Mix</td>
            <td>Brussels GriffonPoodle Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Pug Mix</td>
            <td>Brussels GriffonPug Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Shih Tzu Mix</td>
            <td>Brussels GriffonShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bugg</td>
            <td>Bugg</td>
        </tr>
        <tr>
            <td>Bull Terrier</td>
            <td>Bull Terrier</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Foxhound Mix</td>
            <td>Bull TerrierAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Staffordshire Terrier Mix</td>
            <td>Bull TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Boxer Mix</td>
            <td>Bull TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Labrador Retriever Mix</td>
            <td>Bull TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Staffordshire Bull Terrier Mix</td>
            <td>Bull TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Whippet Mix</td>
            <td>Bull TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>BullBoxer</td>
            <td>BullBoxer</td>
        </tr>
        <tr>
            <td>Bulldog</td>
            <td>Bulldog</td>
        </tr>
        <tr>
            <td>Bulldog-American Pit Bull Terrier Mix</td>
            <td>BulldogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-American Staffordshire Terrier Mix</td>
            <td>BulldogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Basset Hound Mix</td>
            <td>BulldogBasset Hound Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Beagle Mix</td>
            <td>BulldogBeagle Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boston Terrier Mix</td>
            <td>BulldogBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boxer Mix</td>
            <td>BulldogBoxer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Bullmastiff Mix</td>
            <td>BulldogBullmastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Chesapeake Bay Retriever Mix</td>
            <td>BulldogChesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Cocker Spaniel Mix</td>
            <td>BulldogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Dogo Argentino Mix</td>
            <td>BulldogDogo Argentino Mix</td>
        </tr>
        <tr>
            <td>Bulldog-French Bulldog Mix</td>
            <td>BulldogFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shepherd Dog Mix</td>
            <td>BulldogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shorthaired Pointer Mix</td>
            <td>BulldogGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Great Dane Mix</td>
            <td>BulldogGreat Dane Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Labrador Retriever Mix</td>
            <td>BulldogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Mastiff Mix</td>
            <td>BulldogMastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Neapolitan Mastiff Mix</td>
            <td>BulldogNeapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Pug Mix</td>
            <td>BulldogPug Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rhodesian Ridgeback Mix</td>
            <td>BulldogRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rottweiler Mix</td>
            <td>BulldogRottweiler Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Wirehaired Pointing Griffon Mix</td>
            <td>BulldogWirehaired Pointing Griffon Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff</td>
            <td>Bullmastiff</td>
        </tr>
        <tr>
            <td>Bullmastiff- Mix</td>
            <td>Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Pit Bull Terrier Mix</td>
            <td>BullmastiffAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Staffordshire Terrier Mix</td>
            <td>BullmastiffAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Border Collie Mix</td>
            <td>BullmastiffBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Boxer Mix</td>
            <td>BullmastiffBoxer Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bull Terrier Mix</td>
            <td>BullmastiffBull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bulldog Mix</td>
            <td>BullmastiffBulldog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Chinese Shar-Pei Mix</td>
            <td>BullmastiffChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Dogue de Bordeaux Mix</td>
            <td>BullmastiffDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-German Shepherd Dog Mix</td>
            <td>BullmastiffGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Labrador Retriever Mix</td>
            <td>BullmastiffLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Redbone Coonhound Mix</td>
            <td>BullmastiffRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Staffordshire Bull Terrier Mix</td>
            <td>BullmastiffStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier</td>
            <td>Cairn Terrier</td>
        </tr>
        <tr>
            <td>-Cairn Terrier Mix</td>
            <td>Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Airedale Terrier Mix</td>
            <td>Cairn TerrierAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Australian Terrier Mix</td>
            <td>Cairn TerrierAustralian Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Cocker Spaniel Mix</td>
            <td>Cairn TerrierCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-German Shepherd Dog Mix</td>
            <td>Cairn TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Jack Russell Terrier Mix</td>
            <td>Cairn TerrierJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Lhasa Apso Mix</td>
            <td>Cairn TerrierLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Pomeranian Mix</td>
            <td>Cairn TerrierPomeranian Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Poodle Mix</td>
            <td>Cairn TerrierPoodle Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Russell Terrier Mix</td>
            <td>Cairn TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Shih Tzu Mix</td>
            <td>Cairn TerrierShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Smooth Fox Terrier Mix</td>
            <td>Cairn TerrierSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-West Highland White Terrier Mix</td>
            <td>Cairn TerrierWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Yorkshire Terrier Mix</td>
            <td>Cairn TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Canaan Dog</td>
            <td>Canaan Dog</td>
        </tr>
        <tr>
            <td>Canaan Dog- Mix</td>
            <td>Canaan Dog Mix</td>
        </tr>
        <tr>
            <td>Cane Corso</td>
            <td>Cane Corso</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi</td>
            <td>Cardigan Welsh Corgi</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Eskimo Dog Mix</td>
            <td>Cardigan Welsh CorgiAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Pit Bull Terrier Mix</td>
            <td>Cardigan Welsh CorgiAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Staffordshire Terrier Mix</td>
            <td>Cardigan Welsh CorgiAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Cattle Dog Mix</td>
            <td>Cardigan Welsh CorgiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Shepherd Mix</td>
            <td>Cardigan Welsh CorgiAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Beagle Mix</td>
            <td>Cardigan Welsh CorgiBeagle Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Cairn Terrier Mix</td>
            <td>Cardigan Welsh CorgiCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Catahoula Leopard Dog Mix</td>
            <td>Cardigan Welsh CorgiCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-German Shepherd Dog Mix</td>
            <td>Cardigan Welsh CorgiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Labrador Retriever Mix</td>
            <td>Cardigan Welsh CorgiLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Lancashire Heeler Mix</td>
            <td>Cardigan Welsh CorgiLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Pomeranian Mix</td>
            <td>Cardigan Welsh CorgiPomeranian Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Russell Terrier Mix</td>
            <td>Cardigan Welsh CorgiRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Yorkshire Terrier Mix</td>
            <td>Cardigan Welsh CorgiYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog</td>
            <td>Catahoula Leopard Dog</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog- Mix</td>
            <td>Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Leopard Hound Mix</td>
            <td>Catahoula Leopard DogAmerican Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Pit Bull Terrier Mix</td>
            <td>Catahoula Leopard DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Cattle Dog Mix</td>
            <td>Catahoula Leopard DogAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Shepherd Mix</td>
            <td>Catahoula Leopard DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Bluetick Coonhound Mix</td>
            <td>Catahoula Leopard DogBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Border Collie Mix</td>
            <td>Catahoula Leopard DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Boxer Mix</td>
            <td>Catahoula Leopard DogBoxer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-German Shepherd Dog Mix</td>
            <td>Catahoula Leopard DogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Labrador Retriever Mix</td>
            <td>Catahoula Leopard DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Plott Mix</td>
            <td>Catahoula Leopard DogPlott Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Pointer Mix</td>
            <td>Catahoula Leopard DogPointer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Rottweiler Mix</td>
            <td>Catahoula Leopard DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Shetland Sheepdog Mix</td>
            <td>Catahoula Leopard DogShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Siberian Husky Mix</td>
            <td>Catahoula Leopard DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Caucasian Ovcharka</td>
            <td>Caucasian Ovcharka</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel</td>
            <td>Cavalier King Charles Spaniel</td>
        </tr>
        <tr>
            <td>-Cavalier King Charles Spaniel Mix</td>
            <td>Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Australian Shepherd Mix</td>
            <td>Cavalier King Charles SpanielAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Beagle Mix</td>
            <td>Cavalier King Charles SpanielBeagle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Bichon Frise Mix</td>
            <td>Cavalier King Charles SpanielBichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Cocker Spaniel Mix</td>
            <td>Cavalier King Charles SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Coton de Tulear Mix</td>
            <td>Cavalier King Charles SpanielCoton de Tulear Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-English Springer Spaniel Mix</td>
            <td>Cavalier King Charles SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Maltese Mix</td>
            <td>Cavalier King Charles SpanielMaltese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Papillon Mix</td>
            <td>Cavalier King Charles SpanielPapillon Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pekingese Mix</td>
            <td>Cavalier King Charles SpanielPekingese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pomeranian Mix</td>
            <td>Cavalier King Charles SpanielPomeranian Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Poodle Mix</td>
            <td>Cavalier King Charles SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Shih Tzu Mix</td>
            <td>Cavalier King Charles SpanielShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Standard Poodle Mix</td>
            <td>Cavalier King Charles SpanielStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog</td>
            <td>Central Asian Shepherd Dog</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog-Golden Retriever Mix</td>
            <td>Central Asian Shepherd DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cesky Terrier</td>
            <td>Cesky Terrier</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever</td>
            <td>Chesapeake Bay Retriever</td>
        </tr>
        <tr>
            <td>-Chesapeake Bay Retriever Mix</td>
            <td>Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-American Staffordshire Terrier Mix</td>
            <td>Chesapeake Bay RetrieverAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Beagle Mix</td>
            <td>Chesapeake Bay RetrieverBeagle Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-German Shepherd Dog Mix</td>
            <td>Chesapeake Bay RetrieverGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Labrador Retriever Mix</td>
            <td>Chesapeake Bay RetrieverLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Shih Tzu Mix</td>
            <td>Chesapeake Bay RetrieverShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Siberian Husky Mix</td>
            <td>Chesapeake Bay RetrieverSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>Chihuahua</td>
            <td>Chihuahua</td>
        </tr>
        <tr>
            <td>-Chihuahua Mix</td>
            <td>Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Chihuahua- Mix</td>
            <td>Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Airedale Terrier Mix</td>
            <td>ChihuahuaAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Pit Bull Terrier Mix</td>
            <td>ChihuahuaAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Staffordshire Terrier Mix</td>
            <td>ChihuahuaAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Water Spaniel Mix</td>
            <td>ChihuahuaAmerican Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Australian Terrier Mix</td>
            <td>ChihuahuaAustralian Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Beagle Mix</td>
            <td>ChihuahuaBeagle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Bichon Frise Mix</td>
            <td>ChihuahuaBichon Frise Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Boston Terrier Mix</td>
            <td>ChihuahuaBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cairn Terrier Mix</td>
            <td>ChihuahuaCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cardigan Welsh Corgi Mix</td>
            <td>ChihuahuaCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Chinese Crested Mix</td>
            <td>ChihuahuaChinese Crested Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cocker Spaniel Mix</td>
            <td>ChihuahuaCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Dachshund Mix</td>
            <td>ChihuahuaDachshund Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Doberman Pinscher Mix</td>
            <td>ChihuahuaDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Golden Retriever Mix</td>
            <td>ChihuahuaGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Italian Greyhound Mix</td>
            <td>ChihuahuaItalian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Jack Russell Terrier Mix</td>
            <td>ChihuahuaJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Japanese Chin Mix</td>
            <td>ChihuahuaJapanese Chin Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Labrador Retriever Mix</td>
            <td>ChihuahuaLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Lhasa Apso Mix</td>
            <td>ChihuahuaLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Maltese Mix</td>
            <td>ChihuahuaMaltese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Manchester Terrier Mix</td>
            <td>ChihuahuaManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Australian Shepherd Mix</td>
            <td>ChihuahuaMiniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Pinscher Mix</td>
            <td>ChihuahuaMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Schnauzer Mix</td>
            <td>ChihuahuaMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Norwich Terrier Mix</td>
            <td>ChihuahuaNorwich Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Papillon Mix</td>
            <td>ChihuahuaPapillon Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Parson Russell Terrier Mix</td>
            <td>ChihuahuaParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pekingese Mix</td>
            <td>ChihuahuaPekingese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pembroke Welsh Corgi Mix</td>
            <td>ChihuahuaPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pomeranian Mix</td>
            <td>ChihuahuaPomeranian Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Poodle Mix</td>
            <td>ChihuahuaPoodle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pug Mix</td>
            <td>ChihuahuaPug Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Rat Terrier Mix</td>
            <td>ChihuahuaRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Russell Terrier Mix</td>
            <td>ChihuahuaRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Schipperke Mix</td>
            <td>ChihuahuaSchipperke Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shiba Inu Mix</td>
            <td>ChihuahuaShiba Inu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shih Tzu Mix</td>
            <td>ChihuahuaShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Smooth Fox Terrier Mix</td>
            <td>ChihuahuaSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Toy Fox Terrier Mix</td>
            <td>ChihuahuaToy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Whippet Mix</td>
            <td>ChihuahuaWhippet Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Wire Fox Terrier Mix</td>
            <td>ChihuahuaWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Xoloitzcuintli Mix</td>
            <td>ChihuahuaXoloitzcuintli Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Yorkshire Terrier Mix</td>
            <td>ChihuahuaYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested</td>
            <td>Chinese Crested</td>
        </tr>
        <tr>
            <td>Chinese Crested-Chihuahua Mix</td>
            <td>Chinese CrestedChihuahua Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Jack Russell Terrier Mix</td>
            <td>Chinese CrestedJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Lhasa Apso Mix</td>
            <td>Chinese CrestedLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Maltese Mix</td>
            <td>Chinese CrestedMaltese Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Papillon Mix</td>
            <td>Chinese CrestedPapillon Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Poodle Mix</td>
            <td>Chinese CrestedPoodle Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Pug Mix</td>
            <td>Chinese CrestedPug Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Russell Terrier Mix</td>
            <td>Chinese CrestedRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei</td>
            <td>Chinese SharPei</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei- Mix</td>
            <td>Chinese SharPei Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-American Pit Bull Terrier Mix</td>
            <td>Chinese SharPeiAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Australian Cattle Dog Mix</td>
            <td>Chinese SharPeiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Basset Hound Mix</td>
            <td>Chinese SharPeiBasset Hound Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Boerboel Mix</td>
            <td>Chinese SharPeiBoerboel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Cocker Spaniel Mix</td>
            <td>Chinese SharPeiCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-German Shepherd Dog Mix</td>
            <td>Chinese SharPeiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Great Dane Mix</td>
            <td>Chinese SharPeiGreat Dane Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Labrador Retriever Mix</td>
            <td>Chinese SharPeiLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Pug Mix</td>
            <td>Chinese SharPeiPug Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Staffordshire Bull Terrier Mix</td>
            <td>Chinese SharPeiStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinook</td>
            <td>Chinook</td>
        </tr>
        <tr>
            <td>Chinook-German Shepherd Dog Mix</td>
            <td>ChinookGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow</td>
            <td>Chow Chow</td>
        </tr>
        <tr>
            <td>Chow Chow-American Pit Bull Terrier Mix</td>
            <td>Chow ChowAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Australian Shepherd Mix</td>
            <td>Chow ChowAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Catahoula Leopard Dog Mix</td>
            <td>Chow ChowCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Cocker Spaniel Mix</td>
            <td>Chow ChowCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Collie Mix</td>
            <td>Chow ChowCollie Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-German Shepherd Dog Mix</td>
            <td>Chow ChowGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Golden Retriever Mix</td>
            <td>Chow ChowGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Keeshond Mix</td>
            <td>Chow ChowKeeshond Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Labrador Retriever Mix</td>
            <td>Chow ChowLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Newfoundland Mix</td>
            <td>Chow ChowNewfoundland Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Norfolk Terrier Mix</td>
            <td>Chow ChowNorfolk Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Pembroke Welsh Corgi Mix</td>
            <td>Chow ChowPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Poodle Mix</td>
            <td>Chow ChowPoodle Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Rottweiler Mix</td>
            <td>Chow ChowRottweiler Mix</td>
        </tr>
        <tr>
            <td>Cirneco dell&quot;Etna</td>
            <td>Cirneco dell&quot;Etna</td>
        </tr>
        <tr>
            <td>Clumber Spaniel</td>
            <td>Clumber Spaniel</td>
        </tr>
        <tr>
            <td>Clumber Spaniel-English Springer Spaniel Mix</td>
            <td>Clumber SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cockapoo</td>
            <td>Cockapoo</td>
        </tr>
        <tr>
            <td>Cocker Spaniel</td>
            <td>Cocker Spaniel</td>
        </tr>
        <tr>
            <td>-Cocker Spaniel Mix</td>
            <td>Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Bichon Frise Mix</td>
            <td>Cocker SpanielBichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Boxer Mix</td>
            <td>Cocker SpanielBoxer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Cavalier King Charles Spaniel Mix</td>
            <td>Cocker SpanielCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Chow Chow Mix</td>
            <td>Cocker SpanielChow Chow Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Dachshund Mix</td>
            <td>Cocker SpanielDachshund Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Doberman Pinscher Mix</td>
            <td>Cocker SpanielDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Cocker Spaniel Mix</td>
            <td>Cocker SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Springer Spaniel Mix</td>
            <td>Cocker SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Golden Retriever Mix</td>
            <td>Cocker SpanielGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Labrador Retriever Mix</td>
            <td>Cocker SpanielLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Maltese Mix</td>
            <td>Cocker SpanielMaltese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Pinscher Mix</td>
            <td>Cocker SpanielMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Schnauzer Mix</td>
            <td>Cocker SpanielMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pekingese Mix</td>
            <td>Cocker SpanielPekingese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pomeranian Mix</td>
            <td>Cocker SpanielPomeranian Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Poodle Mix</td>
            <td>Cocker SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pug Mix</td>
            <td>Cocker SpanielPug Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Rat Terrier Mix</td>
            <td>Cocker SpanielRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shetland Sheepdog Mix</td>
            <td>Cocker SpanielShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shih Tzu Mix</td>
            <td>Cocker SpanielShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Standard Schnauzer Mix</td>
            <td>Cocker SpanielStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Tibetan Spaniel Mix</td>
            <td>Cocker SpanielTibetan Spaniel Mix</td>
        </tr>
        <tr>
            <td>Collie</td>
            <td>Collie</td>
        </tr>
        <tr>
            <td>-Collie Mix</td>
            <td>Collie Mix</td>
        </tr>
        <tr>
            <td>Collie- Mix</td>
            <td>Collie Mix</td>
        </tr>
        <tr>
            <td>Collie-American Foxhound Mix</td>
            <td>CollieAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>Collie-Anatolian Shepherd Dog Mix</td>
            <td>CollieAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Australian Cattle Dog Mix</td>
            <td>CollieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Belgian Malinois Mix</td>
            <td>CollieBelgian Malinois Mix</td>
        </tr>
        <tr>
            <td>Collie-Boxer Mix</td>
            <td>CollieBoxer Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shepherd Dog Mix</td>
            <td>CollieGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shorthaired Pointer Mix</td>
            <td>CollieGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Collie-Golden Retriever Mix</td>
            <td>CollieGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Labrador Retriever Mix</td>
            <td>CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Shetland Sheepdog Mix</td>
            <td>CollieShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear</td>
            <td>Coton de Tulear</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Chow Chow Mix</td>
            <td>Coton de TulearChow Chow Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Poodle Mix</td>
            <td>Coton de TulearPoodle Mix</td>
        </tr>
        <tr>
            <td>Curly-Coated Retriever</td>
            <td>CurlyCoated Retriever</td>
        </tr>
        <tr>
            <td>Czechoslovakian Vlcak</td>
            <td>Czechoslovakian Vlcak</td>
        </tr>
        <tr>
            <td>Dachshund</td>
            <td>Dachshund</td>
        </tr>
        <tr>
            <td>Dachshund- Mix</td>
            <td>Dachshund Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Pit Bull Terrier Mix</td>
            <td>DachshundAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Staffordshire Terrier Mix</td>
            <td>DachshundAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Basset Hound Mix</td>
            <td>DachshundBasset Hound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Beagle Mix</td>
            <td>DachshundBeagle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Bichon Frise Mix</td>
            <td>DachshundBichon Frise Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Black Russian Terrier Mix</td>
            <td>DachshundBlack Russian Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Boston Terrier Mix</td>
            <td>DachshundBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cardigan Welsh Corgi Mix</td>
            <td>DachshundCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Chihuahua Mix</td>
            <td>DachshundChihuahua Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cocker Spaniel Mix</td>
            <td>DachshundCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Doberman Pinscher Mix</td>
            <td>DachshundDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Flat-Coated Retriever Mix</td>
            <td>DachshundFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-French Bulldog Mix</td>
            <td>DachshundFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Pinscher Mix</td>
            <td>DachshundGerman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shepherd Dog Mix</td>
            <td>DachshundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shorthaired Pointer Mix</td>
            <td>DachshundGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Glen of Imaal Terrier Mix</td>
            <td>DachshundGlen of Imaal Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Golden Retriever Mix</td>
            <td>DachshundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Italian Greyhound Mix</td>
            <td>DachshundItalian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Jack Russell Terrier Mix</td>
            <td>DachshundJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Labrador Retriever Mix</td>
            <td>DachshundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Maltese Mix</td>
            <td>DachshundMaltese Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Pinscher Mix</td>
            <td>DachshundMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Schnauzer Mix</td>
            <td>DachshundMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Parson Russell Terrier Mix</td>
            <td>DachshundParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pembroke Welsh Corgi Mix</td>
            <td>DachshundPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pomeranian Mix</td>
            <td>DachshundPomeranian Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Poodle Mix</td>
            <td>DachshundPoodle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pug Mix</td>
            <td>DachshundPug Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Rat Terrier Mix</td>
            <td>DachshundRat Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Russell Terrier Mix</td>
            <td>DachshundRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Scottish Terrier Mix</td>
            <td>DachshundScottish Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Shih Tzu Mix</td>
            <td>DachshundShih Tzu Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Staffordshire Bull Terrier Mix</td>
            <td>DachshundStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Wire Fox Terrier Mix</td>
            <td>DachshundWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Yorkshire Terrier Mix</td>
            <td>DachshundYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian</td>
            <td>Dalmatian</td>
        </tr>
        <tr>
            <td>Dalmatian-American Pit Bull Terrier Mix</td>
            <td>DalmatianAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Cattle Dog Mix</td>
            <td>DalmatianAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Shepherd Mix</td>
            <td>DalmatianAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Beagle Mix</td>
            <td>DalmatianBeagle Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Border Collie Mix</td>
            <td>DalmatianBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Great Pyrenees Mix</td>
            <td>DalmatianGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Labrador Retriever Mix</td>
            <td>DalmatianLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier</td>
            <td>Dandie Dinmont Terrier</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier-Yorkshire Terrier Mix</td>
            <td>Dandie Dinmont TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog</td>
            <td>DanishSwedish Farmdog</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog-Czechoslovakian Vlcak Mix</td>
            <td>DanishSwedish FarmdogCzechoslovakian Vlcak Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund</td>
            <td>Deutscher Wachtelhund</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund- Mix</td>
            <td>Deutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund-Newfoundland Mix</td>
            <td>Deutscher WachtelhundNewfoundland Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher</td>
            <td>Doberman Pinscher</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-American Staffordshire Terrier Mix</td>
            <td>Doberman PinscherAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beagle Mix</td>
            <td>Doberman PinscherBeagle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beauceron Mix</td>
            <td>Doberman PinscherBeauceron Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Black and Tan Coonhound Mix</td>
            <td>Doberman PinscherBlack and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Boxer Mix</td>
            <td>Doberman PinscherBoxer Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Catahoula Leopard Dog Mix</td>
            <td>Doberman PinscherCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Dalmatian Mix</td>
            <td>Doberman PinscherDalmatian Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-German Shepherd Dog Mix</td>
            <td>Doberman PinscherGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Greyhound Mix</td>
            <td>Doberman PinscherGreyhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Labrador Retriever Mix</td>
            <td>Doberman PinscherLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Poodle Mix</td>
            <td>Doberman PinscherPoodle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Pug Mix</td>
            <td>Doberman PinscherPug Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Rottweiler Mix</td>
            <td>Doberman PinscherRottweiler Mix</td>
        </tr>
        <tr>
            <td>Dogo Argentino</td>
            <td>Dogo Argentino</td>
        </tr>
        <tr>
            <td>Dogo Argentino-American Pit Bull Terrier Mix</td>
            <td>Dogo ArgentinoAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux</td>
            <td>Dogue de Bordeaux</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-American Pit Bull Terrier Mix</td>
            <td>Dogue de BordeauxAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Boxer Mix</td>
            <td>Dogue de BordeauxBoxer Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Labrador Retriever Mix</td>
            <td>Dogue de BordeauxLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Drentsche Patrijshond</td>
            <td>Drentsche Patrijshond</td>
        </tr>
        <tr>
            <td>Dutch Shepherd</td>
            <td>Dutch Shepherd</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Appenzeller Sennenhunde Mix</td>
            <td>Dutch ShepherdAppenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Labrador Retriever Mix</td>
            <td>Dutch ShepherdLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Siberian Husky Mix</td>
            <td>Dutch ShepherdSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel</td>
            <td>English Cocker Spaniel</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Cocker Spaniel Mix</td>
            <td>English Cocker SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Poodle Mix</td>
            <td>English Cocker SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>English Foxhound</td>
            <td>English Foxhound</td>
        </tr>
        <tr>
            <td>English Foxhound-Labrador Retriever Mix</td>
            <td>English FoxhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter</td>
            <td>English Setter</td>
        </tr>
        <tr>
            <td>English Setter- Mix</td>
            <td>English Setter Mix</td>
        </tr>
        <tr>
            <td>English Setter-Beagle Mix</td>
            <td>English SetterBeagle Mix</td>
        </tr>
        <tr>
            <td>English Setter-Border Collie Mix</td>
            <td>English SetterBorder Collie Mix</td>
        </tr>
        <tr>
            <td>English Setter-Brittany Mix</td>
            <td>English SetterBrittany Mix</td>
        </tr>
        <tr>
            <td>English Setter-Dalmatian Mix</td>
            <td>English SetterDalmatian Mix</td>
        </tr>
        <tr>
            <td>English Setter-English Springer Spaniel Mix</td>
            <td>English SetterEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Setter-Labrador Retriever Mix</td>
            <td>English SetterLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter-Pointer Mix</td>
            <td>English SetterPointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel</td>
            <td>English Springer Spaniel</td>
        </tr>
        <tr>
            <td>English Springer Spaniel- Mix</td>
            <td>English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Australian Cattle Dog Mix</td>
            <td>English Springer SpanielAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Border Collie Mix</td>
            <td>English Springer SpanielBorder Collie Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Cocker Spaniel Mix</td>
            <td>English Springer SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Dalmatian Mix</td>
            <td>English Springer SpanielDalmatian Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-English Cocker Spaniel Mix</td>
            <td>English Springer SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-German Shepherd Dog Mix</td>
            <td>English Springer SpanielGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Jack Russell Terrier Mix</td>
            <td>English Springer SpanielJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Labrador Retriever Mix</td>
            <td>English Springer SpanielLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Pointer Mix</td>
            <td>English Springer SpanielPointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Poodle Mix</td>
            <td>English Springer SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Standard Poodle Mix</td>
            <td>English Springer SpanielStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>English Toy Spaniel</td>
            <td>English Toy Spaniel</td>
        </tr>
        <tr>
            <td>Entlebucher Mountain Dog</td>
            <td>Entlebucher Mountain Dog</td>
        </tr>
        <tr>
            <td>Estrela Mountain Dog</td>
            <td>Estrela Mountain Dog</td>
        </tr>
        <tr>
            <td>Eurasier</td>
            <td>Eurasier</td>
        </tr>
        <tr>
            <td>Field Spaniel</td>
            <td>Field Spaniel</td>
        </tr>
        <tr>
            <td>Finnish Lapphund</td>
            <td>Finnish Lapphund</td>
        </tr>
        <tr>
            <td>Finnish Spitz</td>
            <td>Finnish Spitz</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever</td>
            <td>FlatCoated Retriever</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever- Mix</td>
            <td>FlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Border Collie Mix</td>
            <td>FlatCoated RetrieverBorder Collie Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Irish Water Spaniel Mix</td>
            <td>FlatCoated RetrieverIrish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Labrador Retriever Mix</td>
            <td>FlatCoated RetrieverLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Portuguese Water Dog Mix</td>
            <td>FlatCoated RetrieverPortuguese Water Dog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog</td>
            <td>French Bulldog</td>
        </tr>
        <tr>
            <td>French Bulldog-Boston Terrier Mix</td>
            <td>French BulldogBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Bulldog Mix</td>
            <td>French BulldogBulldog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Havanese Mix</td>
            <td>French BulldogHavanese Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Pug Mix</td>
            <td>French BulldogPug Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Shih Tzu Mix</td>
            <td>French BulldogShih Tzu Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Staffordshire Bull Terrier Mix</td>
            <td>French BulldogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>French Spaniel</td>
            <td>French Spaniel</td>
        </tr>
        <tr>
            <td>French Spaniel-German Shorthaired Pointer Mix</td>
            <td>French SpanielGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer</td>
            <td>German Longhaired Pointer</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer-Pointer Mix</td>
            <td>German Longhaired PointerPointer Mix</td>
        </tr>
        <tr>
            <td>German Pinscher</td>
            <td>German Pinscher</td>
        </tr>
        <tr>
            <td>German Pinscher-Weimaraner Mix</td>
            <td>German PinscherWeimaraner Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog</td>
            <td>German Shepherd Dog</td>
        </tr>
        <tr>
            <td>-German Shepherd Dog Mix</td>
            <td>German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog- Mix</td>
            <td>German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Akita Mix</td>
            <td>German Shepherd DogAkita Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Alaskan Malamute Mix</td>
            <td>German Shepherd DogAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Eskimo Dog Mix</td>
            <td>German Shepherd DogAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Pit Bull Terrier Mix</td>
            <td>German Shepherd DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Staffordshire Terrier Mix</td>
            <td>German Shepherd DogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Cattle Dog Mix</td>
            <td>German Shepherd DogAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Kelpie Mix</td>
            <td>German Shepherd DogAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Shepherd Mix</td>
            <td>German Shepherd DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Basenji Mix</td>
            <td>German Shepherd DogBasenji Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Basset Hound Mix</td>
            <td>German Shepherd DogBasset Hound Mix</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">2006 rows, truncated to displaylimit of 1000</span>



That was helpful, but you'll still notice some issues with the output.

First, the leading dashes are indeed removed in the breed\_fixed column,
but now the dashes used to separate breeds in entries like 'French
Bulldog-Boston Terrier Mix' are missing as well. So REPLACE isn't the
right choice to selectively remove leading dashes.

Perhaps we could try using the TRIM function:

http://www.w3resource.com/mysql/string-functions/mysql-trim-function.php

.. code:: sql

    SELECT DISTINCT breed, TRIM(LEADING '-' FROM breed) AS breed_fixed
    FROM dogs
    ORDER BY breed_fixed

**Try the query written above yourself, and inspect the output
carefully:**

.. code:: ipython3

    %%sql
    SELECT DISTINCT breed, TRIM(LEADING '-' FROM breed) AS breed_fixed
    FROM dogs
    ORDER BY breed_fixed;


.. parsed-literal::

    2006 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>breed</th>
            <th>breed_fixed</th>
        </tr>
        <tr>
            <td>Affenpinscher</td>
            <td>Affenpinscher</td>
        </tr>
        <tr>
            <td>Affenpinscher-Afghan Hound Mix</td>
            <td>Affenpinscher-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Airedale Terrier Mix</td>
            <td>Affenpinscher-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Alaskan Malamute Mix</td>
            <td>Affenpinscher-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-American English Coonhound Mix</td>
            <td>Affenpinscher-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Brussels Griffon Mix</td>
            <td>Affenpinscher-Brussels Griffon Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Poodle Mix</td>
            <td>Affenpinscher-Poodle Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Rat Terrier Mix</td>
            <td>Affenpinscher-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Affenpinscher-Spanish Water Dog Mix</td>
            <td>Affenpinscher-Spanish Water Dog Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound</td>
            <td>Afghan Hound</td>
        </tr>
        <tr>
            <td>Afghan Hound-Affenpinscher Mix</td>
            <td>Afghan Hound-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Airedale Terrier Mix</td>
            <td>Afghan Hound-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Akita Mix</td>
            <td>Afghan Hound-Akita Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Bloodhound Mix</td>
            <td>Afghan Hound-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Border Collie Mix</td>
            <td>Afghan Hound-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Afghan Hound-Golden Retriever Mix</td>
            <td>Afghan Hound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier</td>
            <td>Airedale Terrier</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Afghan Hound Mix</td>
            <td>Airedale Terrier-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Border Collie Mix</td>
            <td>Airedale Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Catahoula Leopard Dog Mix</td>
            <td>Airedale Terrier-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shepherd Dog Mix</td>
            <td>Airedale Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-German Shorthaired Pointer Mix</td>
            <td>Airedale Terrier-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Golden Retriever Mix</td>
            <td>Airedale Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Labrador Retriever Mix</td>
            <td>Airedale Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Airedale Terrier-Portuguese Podengo Pequeno Mix</td>
            <td>Airedale Terrier-Portuguese Podengo Pequeno Mix</td>
        </tr>
        <tr>
            <td>Akita</td>
            <td>Akita</td>
        </tr>
        <tr>
            <td>Akita- Mix</td>
            <td>Akita- Mix</td>
        </tr>
        <tr>
            <td>Akita-Affenpinscher Mix</td>
            <td>Akita-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Akita-Afghan Hound Mix</td>
            <td>Akita-Afghan Hound Mix</td>
        </tr>
        <tr>
            <td>Akita-Airedale Terrier Mix</td>
            <td>Akita-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-American Pit Bull Terrier Mix</td>
            <td>Akita-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Akita-Bearded Collie Mix</td>
            <td>Akita-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Akita-Belgian Tervuren Mix</td>
            <td>Akita-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Akita-Bernese Mountain Dog Mix</td>
            <td>Akita-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-German Shepherd Dog Mix</td>
            <td>Akita-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Akita-Labrador Retriever Mix</td>
            <td>Akita-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Akita-Siberian Husky Mix</td>
            <td>Akita-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute</td>
            <td>Alaskan Malamute</td>
        </tr>
        <tr>
            <td>Alaskan Malamute- Mix</td>
            <td>Alaskan Malamute- Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-American Pit Bull Terrier Mix</td>
            <td>Alaskan Malamute-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Australian Kelpie Mix</td>
            <td>Alaskan Malamute-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Beagle Mix</td>
            <td>Alaskan Malamute-Beagle Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Bernese Mountain Dog Mix</td>
            <td>Alaskan Malamute-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Border Collie Mix</td>
            <td>Alaskan Malamute-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Collie Mix</td>
            <td>Alaskan Malamute-Collie Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-English Cocker Spaniel Mix</td>
            <td>Alaskan Malamute-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-German Shepherd Dog Mix</td>
            <td>Alaskan Malamute-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Labrador Retriever Mix</td>
            <td>Alaskan Malamute-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Pomeranian Mix</td>
            <td>Alaskan Malamute-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Alaskan Malamute-Siberian Husky Mix</td>
            <td>Alaskan Malamute-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound</td>
            <td>American English Coonhound</td>
        </tr>
        <tr>
            <td>American English Coonhound-Golden Retriever Mix</td>
            <td>American English Coonhound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Redbone Coonhound Mix</td>
            <td>American English Coonhound-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Rhodesian Ridgeback Mix</td>
            <td>American English Coonhound-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American English Coonhound-Weimaraner Mix</td>
            <td>American English Coonhound-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog</td>
            <td>American Eskimo Dog</td>
        </tr>
        <tr>
            <td>-American Eskimo Dog Mix</td>
            <td>American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog- Mix</td>
            <td>American Eskimo Dog- Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Australian Shepherd Mix</td>
            <td>American Eskimo Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Border Collie Mix</td>
            <td>American Eskimo Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Chihuahua Mix</td>
            <td>American Eskimo Dog-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Cocker Spaniel Mix</td>
            <td>American Eskimo Dog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Collie Mix</td>
            <td>American Eskimo Dog-Collie Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-English Springer Spaniel Mix</td>
            <td>American Eskimo Dog-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Golden Retriever Mix</td>
            <td>American Eskimo Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Papillon Mix</td>
            <td>American Eskimo Dog-Papillon Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pembroke Welsh Corgi Mix</td>
            <td>American Eskimo Dog-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Pomeranian Mix</td>
            <td>American Eskimo Dog-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Poodle Mix</td>
            <td>American Eskimo Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Russell Terrier Mix</td>
            <td>American Eskimo Dog-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Shiba Inu Mix</td>
            <td>American Eskimo Dog-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Siberian Husky Mix</td>
            <td>American Eskimo Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Eskimo Dog-Staffordshire Bull Terrier Mix</td>
            <td>American Eskimo Dog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Foxhound</td>
            <td>American Foxhound</td>
        </tr>
        <tr>
            <td>American Foxhound- Mix</td>
            <td>American Foxhound- Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Anatolian Shepherd Dog Mix</td>
            <td>American Foxhound-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Beagle Mix</td>
            <td>American Foxhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-German Shepherd Dog Mix</td>
            <td>American Foxhound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Labrador Retriever Mix</td>
            <td>American Foxhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Foxhound-Pointer Mix</td>
            <td>American Foxhound-Pointer Mix</td>
        </tr>
        <tr>
            <td>American Hairless Terrier</td>
            <td>American Hairless Terrier</td>
        </tr>
        <tr>
            <td>American Hairless Terrier-Shetland Sheepdog Mix</td>
            <td>American Hairless Terrier-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>American Leopard Hound</td>
            <td>American Leopard Hound</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier</td>
            <td>American Pit Bull Terrier</td>
        </tr>
        <tr>
            <td>-American Pit Bull Terrier Mix</td>
            <td>American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier- Mix</td>
            <td>American Pit Bull Terrier- Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American English Coonhound Mix</td>
            <td>American Pit Bull Terrier-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Leopard Hound Mix</td>
            <td>American Pit Bull Terrier-American Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-American Staffordshire Terrier Mix</td>
            <td>American Pit Bull Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Cattle Dog Mix</td>
            <td>American Pit Bull Terrier-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Australian Shepherd Mix</td>
            <td>American Pit Bull Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Beagle Mix</td>
            <td>American Pit Bull Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Border Collie Mix</td>
            <td>American Pit Bull Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boston Terrier Mix</td>
            <td>American Pit Bull Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Boxer Mix</td>
            <td>American Pit Bull Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Brittany Mix</td>
            <td>American Pit Bull Terrier-Brittany Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bull Terrier Mix</td>
            <td>American Pit Bull Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bulldog Mix</td>
            <td>American Pit Bull Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Bullmastiff Mix</td>
            <td>American Pit Bull Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cane Corso Mix</td>
            <td>American Pit Bull Terrier-Cane Corso Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Cardigan Welsh Corgi Mix</td>
            <td>American Pit Bull Terrier-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Chinese Shar-Pei Mix</td>
            <td>American Pit Bull Terrier-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Doberman Pinscher Mix</td>
            <td>American Pit Bull Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Dogue de Bordeaux Mix</td>
            <td>American Pit Bull Terrier-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-German Shepherd Dog Mix</td>
            <td>American Pit Bull Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Dane Mix</td>
            <td>American Pit Bull Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Great Pyrenees Mix</td>
            <td>American Pit Bull Terrier-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Greyhound Mix</td>
            <td>American Pit Bull Terrier-Greyhound Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Labrador Retriever Mix</td>
            <td>American Pit Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Mastiff Mix</td>
            <td>American Pit Bull Terrier-Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Parson Russell Terrier Mix</td>
            <td>American Pit Bull Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Plott Mix</td>
            <td>American Pit Bull Terrier-Plott Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Pointer Mix</td>
            <td>American Pit Bull Terrier-Pointer Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rhodesian Ridgeback Mix</td>
            <td>American Pit Bull Terrier-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Rottweiler Mix</td>
            <td>American Pit Bull Terrier-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Siberian Husky Mix</td>
            <td>American Pit Bull Terrier-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Staffordshire Bull Terrier Mix</td>
            <td>American Pit Bull Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Treeing Tennessee Brindle Mix</td>
            <td>American Pit Bull Terrier-Treeing Tennessee Brindle Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Vizsla Mix</td>
            <td>American Pit Bull Terrier-Vizsla Mix</td>
        </tr>
        <tr>
            <td>American Pit Bull Terrier-Whippet Mix</td>
            <td>American Pit Bull Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier</td>
            <td>American Staffordshire Terrier</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier- Mix</td>
            <td>American Staffordshire Terrier- Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Airedale Terrier Mix</td>
            <td>American Staffordshire Terrier-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-American Pit Bull Terrier Mix</td>
            <td>American Staffordshire Terrier-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Australian Shepherd Mix</td>
            <td>American Staffordshire Terrier-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Beagle Mix</td>
            <td>American Staffordshire Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Border Collie Mix</td>
            <td>American Staffordshire Terrier-Border Collie Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boston Terrier Mix</td>
            <td>American Staffordshire Terrier-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Boxer Mix</td>
            <td>American Staffordshire Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bull Terrier Mix</td>
            <td>American Staffordshire Terrier-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bulldog Mix</td>
            <td>American Staffordshire Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Bullmastiff Mix</td>
            <td>American Staffordshire Terrier-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Catahoula Leopard Dog Mix</td>
            <td>American Staffordshire Terrier-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chinese Shar-Pei Mix</td>
            <td>American Staffordshire Terrier-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Chow Chow Mix</td>
            <td>American Staffordshire Terrier-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dalmatian Mix</td>
            <td>American Staffordshire Terrier-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Doberman Pinscher Mix</td>
            <td>American Staffordshire Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogo Argentino Mix</td>
            <td>American Staffordshire Terrier-Dogo Argentino Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Dogue de Bordeaux Mix</td>
            <td>American Staffordshire Terrier-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Shepherd Dog Mix</td>
            <td>American Staffordshire Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-German Wirehaired Pointer Mix</td>
            <td>American Staffordshire Terrier-German Wirehaired Pointer Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Golden Retriever Mix</td>
            <td>American Staffordshire Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Gordon Setter Mix</td>
            <td>American Staffordshire Terrier-Gordon Setter Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Dane Mix</td>
            <td>American Staffordshire Terrier-Great Dane Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Great Pyrenees Mix</td>
            <td>American Staffordshire Terrier-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Greyhound Mix</td>
            <td>American Staffordshire Terrier-Greyhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Labrador Retriever Mix</td>
            <td>American Staffordshire Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Lancashire Heeler Mix</td>
            <td>American Staffordshire Terrier-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Mastiff Mix</td>
            <td>American Staffordshire Terrier-Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Miniature Bull Terrier Mix</td>
            <td>American Staffordshire Terrier-Miniature Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Neapolitan Mastiff Mix</td>
            <td>American Staffordshire Terrier-Neapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Portuguese Podengo Mix</td>
            <td>American Staffordshire Terrier-Portuguese Podengo Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Redbone Coonhound Mix</td>
            <td>American Staffordshire Terrier-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Rhodesian Ridgeback Mix</td>
            <td>American Staffordshire Terrier-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Staffordshire Bull Terrier Mix</td>
            <td>American Staffordshire Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Treeing Walker Coonhound Mix</td>
            <td>American Staffordshire Terrier-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Weimaraner Mix</td>
            <td>American Staffordshire Terrier-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>American Staffordshire Terrier-Whippet Mix</td>
            <td>American Staffordshire Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>American Water Spaniel</td>
            <td>American Water Spaniel</td>
        </tr>
        <tr>
            <td>American Water Spaniel-Dachshund Mix</td>
            <td>American Water Spaniel-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog</td>
            <td>Anatolian Shepherd Dog</td>
        </tr>
        <tr>
            <td>-Anatolian Shepherd Dog Mix</td>
            <td>Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Border Collie Mix</td>
            <td>Anatolian Shepherd Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Great Pyrenees Mix</td>
            <td>Anatolian Shepherd Dog-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Labrador Retriever Mix</td>
            <td>Anatolian Shepherd Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Anatolian Shepherd Dog-Mastiff Mix</td>
            <td>Anatolian Shepherd Dog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde</td>
            <td>Appenzeller Sennenhunde</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde- Mix</td>
            <td>Appenzeller Sennenhunde- Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Border Collie Mix</td>
            <td>Appenzeller Sennenhunde-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Appenzeller Sennenhunde-Collie Mix</td>
            <td>Appenzeller Sennenhunde-Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog</td>
            <td>Australian Cattle Dog</td>
        </tr>
        <tr>
            <td>-Australian Cattle Dog Mix</td>
            <td>Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog- Mix</td>
            <td>Australian Cattle Dog- Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Pit Bull Terrier Mix</td>
            <td>Australian Cattle Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-American Staffordshire Terrier Mix</td>
            <td>Australian Cattle Dog-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Anatolian Shepherd Dog Mix</td>
            <td>Australian Cattle Dog-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Kelpie Mix</td>
            <td>Australian Cattle Dog-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Australian Shepherd Mix</td>
            <td>Australian Cattle Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Basenji Mix</td>
            <td>Australian Cattle Dog-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Beagle Mix</td>
            <td>Australian Cattle Dog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bearded Collie Mix</td>
            <td>Australian Cattle Dog-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Belgian Sheepdog Mix</td>
            <td>Australian Cattle Dog-Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bernese Mountain Dog Mix</td>
            <td>Australian Cattle Dog-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bluetick Coonhound Mix</td>
            <td>Australian Cattle Dog-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Border Collie Mix</td>
            <td>Australian Cattle Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Boxer Mix</td>
            <td>Australian Cattle Dog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Bull Terrier Mix</td>
            <td>Australian Cattle Dog-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cardigan Welsh Corgi Mix</td>
            <td>Australian Cattle Dog-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Catahoula Leopard Dog Mix</td>
            <td>Australian Cattle Dog-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Chow Chow Mix</td>
            <td>Australian Cattle Dog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Cocker Spaniel Mix</td>
            <td>Australian Cattle Dog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Curly-Coated Retriever Mix</td>
            <td>Australian Cattle Dog-Curly-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Doberman Pinscher Mix</td>
            <td>Australian Cattle Dog-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Longhaired Pointer Mix</td>
            <td>Australian Cattle Dog-German Longhaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-German Shepherd Dog Mix</td>
            <td>Australian Cattle Dog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Greyhound Mix</td>
            <td>Australian Cattle Dog-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Labrador Retriever Mix</td>
            <td>Australian Cattle Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rat Terrier Mix</td>
            <td>Australian Cattle Dog-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Redbone Coonhound Mix</td>
            <td>Australian Cattle Dog-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Rottweiler Mix</td>
            <td>Australian Cattle Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Shetland Sheepdog Mix</td>
            <td>Australian Cattle Dog-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Siberian Husky Mix</td>
            <td>Australian Cattle Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Staffordshire Bull Terrier Mix</td>
            <td>Australian Cattle Dog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Treeing Walker Coonhound Mix</td>
            <td>Australian Cattle Dog-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Australian Cattle Dog-Weimaraner Mix</td>
            <td>Australian Cattle Dog-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie</td>
            <td>Australian Kelpie</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Australian Cattle Dog Mix</td>
            <td>Australian Kelpie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Basenji Mix</td>
            <td>Australian Kelpie-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Border Collie Mix</td>
            <td>Australian Kelpie-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Labrador Retriever Mix</td>
            <td>Australian Kelpie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Miniature Schnauzer Mix</td>
            <td>Australian Kelpie-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Rottweiler Mix</td>
            <td>Australian Kelpie-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Kelpie-Staffordshire Bull Terrier Mix</td>
            <td>Australian Kelpie-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Labradoodle</td>
            <td>Australian Labradoodle</td>
        </tr>
        <tr>
            <td>Australian Labradoodle-Poodle Mix</td>
            <td>Australian Labradoodle-Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd</td>
            <td>Australian Shepherd</td>
        </tr>
        <tr>
            <td>-Australian Shepherd Mix</td>
            <td>Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd- Mix</td>
            <td>Australian Shepherd- Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Alaskan Malamute Mix</td>
            <td>Australian Shepherd-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-American Pit Bull Terrier Mix</td>
            <td>Australian Shepherd-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Australian Cattle Dog Mix</td>
            <td>Australian Shepherd-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Basenji Mix</td>
            <td>Australian Shepherd-Basenji Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Beagle Mix</td>
            <td>Australian Shepherd-Beagle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bearded Collie Mix</td>
            <td>Australian Shepherd-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Bloodhound Mix</td>
            <td>Australian Shepherd-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Border Collie Mix</td>
            <td>Australian Shepherd-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cardigan Welsh Corgi Mix</td>
            <td>Australian Shepherd-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Catahoula Leopard Dog Mix</td>
            <td>Australian Shepherd-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Chow Chow Mix</td>
            <td>Australian Shepherd-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Cocker Spaniel Mix</td>
            <td>Australian Shepherd-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Collie Mix</td>
            <td>Australian Shepherd-Collie Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Doberman Pinscher Mix</td>
            <td>Australian Shepherd-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-English Cocker Spaniel Mix</td>
            <td>Australian Shepherd-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Flat-Coated Retriever Mix</td>
            <td>Australian Shepherd-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-German Shepherd Dog Mix</td>
            <td>Australian Shepherd-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Golden Retriever Mix</td>
            <td>Australian Shepherd-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Great Pyrenees Mix</td>
            <td>Australian Shepherd-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Labrador Retriever Mix</td>
            <td>Australian Shepherd-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pembroke Welsh Corgi Mix</td>
            <td>Australian Shepherd-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Poodle Mix</td>
            <td>Australian Shepherd-Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Pug Mix</td>
            <td>Australian Shepherd-Pug Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rhodesian Ridgeback Mix</td>
            <td>Australian Shepherd-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Rottweiler Mix</td>
            <td>Australian Shepherd-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Schipperke Mix</td>
            <td>Australian Shepherd-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shetland Sheepdog Mix</td>
            <td>Australian Shepherd-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shiba Inu Mix</td>
            <td>Australian Shepherd-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Shih Tzu Mix</td>
            <td>Australian Shepherd-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Siberian Husky Mix</td>
            <td>Australian Shepherd-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-St. Bernard Mix</td>
            <td>Australian Shepherd-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Standard Poodle Mix</td>
            <td>Australian Shepherd-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Australian Shepherd-Weimaraner Mix</td>
            <td>Australian Shepherd-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier</td>
            <td>Australian Terrier</td>
        </tr>
        <tr>
            <td>Australian Terrier-Lowchen Mix</td>
            <td>Australian Terrier-Lowchen Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Parson Russell Terrier Mix</td>
            <td>Australian Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Rottweiler Mix</td>
            <td>Australian Terrier-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Australian Terrier-Yorkshire Terrier Mix</td>
            <td>Australian Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Barbet</td>
            <td>Barbet</td>
        </tr>
        <tr>
            <td>Basenji</td>
            <td>Basenji</td>
        </tr>
        <tr>
            <td>Basenji- Mix</td>
            <td>Basenji- Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Staffordshire Terrier Mix</td>
            <td>Basenji-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-American Water Spaniel Mix</td>
            <td>Basenji-American Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-Australian Cattle Dog Mix</td>
            <td>Basenji-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-Beagle Mix</td>
            <td>Basenji-Beagle Mix</td>
        </tr>
        <tr>
            <td>Basenji-Cardigan Welsh Corgi Mix</td>
            <td>Basenji-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basenji-English Springer Spaniel Mix</td>
            <td>Basenji-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shepherd Dog Mix</td>
            <td>Basenji-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basenji-German Shorthaired Pointer Mix</td>
            <td>Basenji-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Basenji-Manchester Terrier Mix</td>
            <td>Basenji-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Russell Terrier Mix</td>
            <td>Basenji-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basenji-Shiba Inu Mix</td>
            <td>Basenji-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Basenji-Siberian Husky Mix</td>
            <td>Basenji-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Basenji-Whippet Mix</td>
            <td>Basenji-Whippet Mix</td>
        </tr>
        <tr>
            <td>Basset Hound</td>
            <td>Basset Hound</td>
        </tr>
        <tr>
            <td>Basset Hound- Mix</td>
            <td>Basset Hound- Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Airedale Terrier Mix</td>
            <td>Basset Hound-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American English Coonhound Mix</td>
            <td>Basset Hound-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Pit Bull Terrier Mix</td>
            <td>Basset Hound-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-American Staffordshire Terrier Mix</td>
            <td>Basset Hound-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Cattle Dog Mix</td>
            <td>Basset Hound-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Australian Shepherd Mix</td>
            <td>Basset Hound-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Beagle Mix</td>
            <td>Basset Hound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Boston Terrier Mix</td>
            <td>Basset Hound-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cardigan Welsh Corgi Mix</td>
            <td>Basset Hound-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Cocker Spaniel Mix</td>
            <td>Basset Hound-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Dachshund Mix</td>
            <td>Basset Hound-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-German Shepherd Dog Mix</td>
            <td>Basset Hound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Great Pyrenees Mix</td>
            <td>Basset Hound-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Labrador Retriever Mix</td>
            <td>Basset Hound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pembroke Welsh Corgi Mix</td>
            <td>Basset Hound-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Pointer Mix</td>
            <td>Basset Hound-Pointer Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Poodle Mix</td>
            <td>Basset Hound-Poodle Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Rottweiler Mix</td>
            <td>Basset Hound-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Russell Terrier Mix</td>
            <td>Basset Hound-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Basset Hound-Staffordshire Bull Terrier Mix</td>
            <td>Basset Hound-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle</td>
            <td>Beagle</td>
        </tr>
        <tr>
            <td>-Beagle Mix</td>
            <td>Beagle Mix</td>
        </tr>
        <tr>
            <td>Beagle- Mix</td>
            <td>Beagle- Mix</td>
        </tr>
        <tr>
            <td>Beagle-American English Coonhound Mix</td>
            <td>Beagle-American English Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Eskimo Dog Mix</td>
            <td>Beagle-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-American Foxhound Mix</td>
            <td>Beagle-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Australian Cattle Dog Mix</td>
            <td>Beagle-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Basset Hound Mix</td>
            <td>Beagle-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bluetick Coonhound Mix</td>
            <td>Beagle-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Collie Mix</td>
            <td>Beagle-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Border Terrier Mix</td>
            <td>Beagle-Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boston Terrier Mix</td>
            <td>Beagle-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Boxer Mix</td>
            <td>Beagle-Boxer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Bulldog Mix</td>
            <td>Beagle-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cavalier King Charles Spaniel Mix</td>
            <td>Beagle-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chihuahua Mix</td>
            <td>Beagle-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chinese Shar-Pei Mix</td>
            <td>Beagle-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Beagle-Chow Chow Mix</td>
            <td>Beagle-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Beagle-Cocker Spaniel Mix</td>
            <td>Beagle-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Beagle-Collie Mix</td>
            <td>Beagle-Collie Mix</td>
        </tr>
        <tr>
            <td>Beagle-Dachshund Mix</td>
            <td>Beagle-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Beagle-German Shepherd Dog Mix</td>
            <td>Beagle-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Golden Retriever Mix</td>
            <td>Beagle-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Greyhound Mix</td>
            <td>Beagle-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Jack Russell Terrier Mix</td>
            <td>Beagle-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Labrador Retriever Mix</td>
            <td>Beagle-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Beagle-Miniature Schnauzer Mix</td>
            <td>Beagle-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Parson Russell Terrier Mix</td>
            <td>Beagle-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pekingese Mix</td>
            <td>Beagle-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pointer Mix</td>
            <td>Beagle-Pointer Mix</td>
        </tr>
        <tr>
            <td>Beagle-Poodle Mix</td>
            <td>Beagle-Poodle Mix</td>
        </tr>
        <tr>
            <td>Beagle-Pug Mix</td>
            <td>Beagle-Pug Mix</td>
        </tr>
        <tr>
            <td>Beagle-Rat Terrier Mix</td>
            <td>Beagle-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Russell Terrier Mix</td>
            <td>Beagle-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Schipperke Mix</td>
            <td>Beagle-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Beagle-Shetland Sheepdog Mix</td>
            <td>Beagle-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Beagle-Siberian Husky Mix</td>
            <td>Beagle-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Beagle-Smooth Fox Terrier Mix</td>
            <td>Beagle-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Toy Fox Terrier Mix</td>
            <td>Beagle-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Beagle-Treeing Walker Coonhound Mix</td>
            <td>Beagle-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Beagle-Whippet Mix</td>
            <td>Beagle-Whippet Mix</td>
        </tr>
        <tr>
            <td>Beaglier</td>
            <td>Beaglier</td>
        </tr>
        <tr>
            <td>Bearded Collie</td>
            <td>Bearded Collie</td>
        </tr>
        <tr>
            <td>Bearded Collie-Beagle Mix</td>
            <td>Bearded Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Bernese Mountain Dog Mix</td>
            <td>Bearded Collie-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Border Collie Mix</td>
            <td>Bearded Collie-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Labrador Retriever Mix</td>
            <td>Bearded Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Shih Tzu Mix</td>
            <td>Bearded Collie-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Soft Coated Wheaten Terrier Mix</td>
            <td>Bearded Collie-Soft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Bearded Collie-Tibetan Terrier Mix</td>
            <td>Bearded Collie-Tibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>Beauceron</td>
            <td>Beauceron</td>
        </tr>
        <tr>
            <td>Beauceron-Rottweiler Mix</td>
            <td>Beauceron-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier</td>
            <td>Bedlington Terrier</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Belgian Laekenois Mix</td>
            <td>Bedlington Terrier-Belgian Laekenois Mix</td>
        </tr>
        <tr>
            <td>Bedlington Terrier-Whippet Mix</td>
            <td>Bedlington Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>Belgian Laekenois</td>
            <td>Belgian Laekenois</td>
        </tr>
        <tr>
            <td>Belgian Malinois</td>
            <td>Belgian Malinois</td>
        </tr>
        <tr>
            <td>Belgian Malinois- Mix</td>
            <td>Belgian Malinois- Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-American Staffordshire Terrier Mix</td>
            <td>Belgian Malinois-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Belgian Tervuren Mix</td>
            <td>Belgian Malinois-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Border Collie Mix</td>
            <td>Belgian Malinois-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chinese Shar-Pei Mix</td>
            <td>Belgian Malinois-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Chow Chow Mix</td>
            <td>Belgian Malinois-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Dutch Shepherd Mix</td>
            <td>Belgian Malinois-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-German Shepherd Dog Mix</td>
            <td>Belgian Malinois-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Labrador Retriever Mix</td>
            <td>Belgian Malinois-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Malinois-Siberian Husky Mix</td>
            <td>Belgian Malinois-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog</td>
            <td>Belgian Sheepdog</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog- Mix</td>
            <td>Belgian Sheepdog- Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Border Collie Mix</td>
            <td>Belgian Sheepdog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Chow Chow Mix</td>
            <td>Belgian Sheepdog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Dutch Shepherd Mix</td>
            <td>Belgian Sheepdog-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-German Shepherd Dog Mix</td>
            <td>Belgian Sheepdog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Golden Retriever Mix</td>
            <td>Belgian Sheepdog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Belgian Sheepdog-Lhasa Apso Mix</td>
            <td>Belgian Sheepdog-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren</td>
            <td>Belgian Tervuren</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Basenji Mix</td>
            <td>Belgian Tervuren-Basenji Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Border Collie Mix</td>
            <td>Belgian Tervuren-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Boston Terrier Mix</td>
            <td>Belgian Tervuren-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Belgian Tervuren-Whippet Mix</td>
            <td>Belgian Tervuren-Whippet Mix</td>
        </tr>
        <tr>
            <td>Bergamasco-Old English Sheepdog Mix</td>
            <td>Bergamasco-Old English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Berger Picard</td>
            <td>Berger Picard</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog</td>
            <td>Bernese Mountain Dog</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Border Collie Mix</td>
            <td>Bernese Mountain Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Chow Chow Mix</td>
            <td>Bernese Mountain Dog-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-English Springer Spaniel Mix</td>
            <td>Bernese Mountain Dog-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Golden Retriever Mix</td>
            <td>Bernese Mountain Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Great Pyrenees Mix</td>
            <td>Bernese Mountain Dog-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Greater Swiss Mountain Dog Mix</td>
            <td>Bernese Mountain Dog-Greater Swiss Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Labrador Retriever Mix</td>
            <td>Bernese Mountain Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Poodle Mix</td>
            <td>Bernese Mountain Dog-Poodle Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Rottweiler Mix</td>
            <td>Bernese Mountain Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bernese Mountain Dog-Standard Poodle Mix</td>
            <td>Bernese Mountain Dog-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise</td>
            <td>Bichon Frise</td>
        </tr>
        <tr>
            <td>-Bichon Frise Mix</td>
            <td>Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise- Mix</td>
            <td>Bichon Frise- Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-American Eskimo Dog Mix</td>
            <td>Bichon Frise-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cavalier King Charles Spaniel Mix</td>
            <td>Bichon Frise-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Chinese Crested Mix</td>
            <td>Bichon Frise-Chinese Crested Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Cocker Spaniel Mix</td>
            <td>Bichon Frise-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Golden Retriever Mix</td>
            <td>Bichon Frise-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Havanese Mix</td>
            <td>Bichon Frise-Havanese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Jack Russell Terrier Mix</td>
            <td>Bichon Frise-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Lhasa Apso Mix</td>
            <td>Bichon Frise-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Maltese Mix</td>
            <td>Bichon Frise-Maltese Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Miniature Schnauzer Mix</td>
            <td>Bichon Frise-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Pomeranian Mix</td>
            <td>Bichon Frise-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Poodle Mix</td>
            <td>Bichon Frise-Poodle Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Shih Tzu Mix</td>
            <td>Bichon Frise-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-West Highland White Terrier Mix</td>
            <td>Bichon Frise-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Bichon Frise-Yorkshire Terrier Mix</td>
            <td>Bichon Frise-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound</td>
            <td>Black and Tan Coonhound</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound- Mix</td>
            <td>Black and Tan Coonhound- Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Beagle Mix</td>
            <td>Black and Tan Coonhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-German Shepherd Dog Mix</td>
            <td>Black and Tan Coonhound-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Golden Retriever Mix</td>
            <td>Black and Tan Coonhound-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Labrador Retriever Mix</td>
            <td>Black and Tan Coonhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Black and Tan Coonhound-Plott Mix</td>
            <td>Black and Tan Coonhound-Plott Mix</td>
        </tr>
        <tr>
            <td>Black Russian Terrier</td>
            <td>Black Russian Terrier</td>
        </tr>
        <tr>
            <td>Bloodhound</td>
            <td>Bloodhound</td>
        </tr>
        <tr>
            <td>Bloodhound-Beagle Mix</td>
            <td>Bloodhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Black and Tan Coonhound Mix</td>
            <td>Bloodhound-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Bull Terrier Mix</td>
            <td>Bloodhound-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Irish Setter Mix</td>
            <td>Bloodhound-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Bloodhound-Labrador Retriever Mix</td>
            <td>Bloodhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound</td>
            <td>Bluetick Coonhound</td>
        </tr>
        <tr>
            <td>-Bluetick Coonhound Mix</td>
            <td>Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Beagle Mix</td>
            <td>Bluetick Coonhound-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-German Shorthaired Pointer Mix</td>
            <td>Bluetick Coonhound-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Jack Russell Terrier Mix</td>
            <td>Bluetick Coonhound-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Pointer Mix</td>
            <td>Bluetick Coonhound-Pointer Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Rottweiler Mix</td>
            <td>Bluetick Coonhound-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bluetick Coonhound-Treeing Walker Coonhound Mix</td>
            <td>Bluetick Coonhound-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boerboel</td>
            <td>Boerboel</td>
        </tr>
        <tr>
            <td>Bolognese</td>
            <td>Bolognese</td>
        </tr>
        <tr>
            <td>Border Collie</td>
            <td>Border Collie</td>
        </tr>
        <tr>
            <td>-Border Collie Mix</td>
            <td>Border Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie- Mix</td>
            <td>Border Collie- Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Affenpinscher Mix</td>
            <td>Border Collie-Affenpinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Akita Mix</td>
            <td>Border Collie-Akita Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Eskimo Dog Mix</td>
            <td>Border Collie-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Foxhound Mix</td>
            <td>Border Collie-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Pit Bull Terrier Mix</td>
            <td>Border Collie-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-American Staffordshire Terrier Mix</td>
            <td>Border Collie-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Cattle Dog Mix</td>
            <td>Border Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Kelpie Mix</td>
            <td>Border Collie-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Australian Shepherd Mix</td>
            <td>Border Collie-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beagle Mix</td>
            <td>Border Collie-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bearded Collie Mix</td>
            <td>Border Collie-Bearded Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Beauceron Mix</td>
            <td>Border Collie-Beauceron Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Sheepdog Mix</td>
            <td>Border Collie-Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Belgian Tervuren Mix</td>
            <td>Border Collie-Belgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bernese Mountain Dog Mix</td>
            <td>Border Collie-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bloodhound Mix</td>
            <td>Border Collie-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bluetick Coonhound Mix</td>
            <td>Border Collie-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Borzoi Mix</td>
            <td>Border Collie-Borzoi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Boxer Mix</td>
            <td>Border Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Brittany Mix</td>
            <td>Border Collie-Brittany Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Bull Terrier Mix</td>
            <td>Border Collie-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cavalier King Charles Spaniel Mix</td>
            <td>Border Collie-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Chow Chow Mix</td>
            <td>Border Collie-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Cocker Spaniel Mix</td>
            <td>Border Collie-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Collie Mix</td>
            <td>Border Collie-Collie Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Dalmatian Mix</td>
            <td>Border Collie-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Cocker Spaniel Mix</td>
            <td>Border Collie-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Setter Mix</td>
            <td>Border Collie-English Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-English Springer Spaniel Mix</td>
            <td>Border Collie-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Field Spaniel Mix</td>
            <td>Border Collie-Field Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Flat-Coated Retriever Mix</td>
            <td>Border Collie-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shepherd Dog Mix</td>
            <td>Border Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-German Shorthaired Pointer Mix</td>
            <td>Border Collie-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Golden Retriever Mix</td>
            <td>Border Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Dane Mix</td>
            <td>Border Collie-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Great Pyrenees Mix</td>
            <td>Border Collie-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Greyhound Mix</td>
            <td>Border Collie-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Icelandic Sheepdog Mix</td>
            <td>Border Collie-Icelandic Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Setter Mix</td>
            <td>Border Collie-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Irish Water Spaniel Mix</td>
            <td>Border Collie-Irish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Jack Russell Terrier Mix</td>
            <td>Border Collie-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Keeshond Mix</td>
            <td>Border Collie-Keeshond Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Kooikerhondje Mix</td>
            <td>Border Collie-Kooikerhondje Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Labrador Retriever Mix</td>
            <td>Border Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Lancashire Heeler Mix</td>
            <td>Border Collie-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Australian Shepherd Mix</td>
            <td>Border Collie-Miniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Miniature Pinscher Mix</td>
            <td>Border Collie-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Newfoundland Mix</td>
            <td>Border Collie-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Parson Russell Terrier Mix</td>
            <td>Border Collie-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pembroke Welsh Corgi Mix</td>
            <td>Border Collie-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pointer Mix</td>
            <td>Border Collie-Pointer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Pomeranian Mix</td>
            <td>Border Collie-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Poodle Mix</td>
            <td>Border Collie-Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rhodesian Ridgeback Mix</td>
            <td>Border Collie-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Rottweiler Mix</td>
            <td>Border Collie-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Saluki Mix</td>
            <td>Border Collie-Saluki Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Shetland Sheepdog Mix</td>
            <td>Border Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Siberian Husky Mix</td>
            <td>Border Collie-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Soft Coated Wheaten Terrier Mix</td>
            <td>Border Collie-Soft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Staffordshire Bull Terrier Mix</td>
            <td>Border Collie-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Poodle Mix</td>
            <td>Border Collie-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Standard Schnauzer Mix</td>
            <td>Border Collie-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Welsh Springer Spaniel Mix</td>
            <td>Border Collie-Welsh Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Collie-West Highland White Terrier Mix</td>
            <td>Border Collie-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Whippet Mix</td>
            <td>Border Collie-Whippet Mix</td>
        </tr>
        <tr>
            <td>Border Collie-Wire Fox Terrier Mix</td>
            <td>Border Collie-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier</td>
            <td>Border Terrier</td>
        </tr>
        <tr>
            <td>Border Terrier- Mix</td>
            <td>Border Terrier- Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Beagle Mix</td>
            <td>Border Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Bernese Mountain Dog Mix</td>
            <td>Border Terrier-Bernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Cairn Terrier Mix</td>
            <td>Border Terrier-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Dachshund Mix</td>
            <td>Border Terrier-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-English Cocker Spaniel Mix</td>
            <td>Border Terrier-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Golden Retriever Mix</td>
            <td>Border Terrier-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Lakeland Terrier Mix</td>
            <td>Border Terrier-Lakeland Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Parson Russell Terrier Mix</td>
            <td>Border Terrier-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Poodle Mix</td>
            <td>Border Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Pug Mix</td>
            <td>Border Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Russell Terrier Mix</td>
            <td>Border Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Shih Tzu Mix</td>
            <td>Border Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Staffordshire Bull Terrier Mix</td>
            <td>Border Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-Standard Schnauzer Mix</td>
            <td>Border Terrier-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Border Terrier-West Highland White Terrier Mix</td>
            <td>Border Terrier-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Borzoi</td>
            <td>Borzoi</td>
        </tr>
        <tr>
            <td>Borzoi-Whippet Mix</td>
            <td>Borzoi-Whippet Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier</td>
            <td>Boston Terrier</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Pit Bull Terrier Mix</td>
            <td>Boston Terrier-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-American Staffordshire Terrier Mix</td>
            <td>Boston Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Beagle Mix</td>
            <td>Boston Terrier-Beagle Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Bulldog Mix</td>
            <td>Boston Terrier-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Chihuahua Mix</td>
            <td>Boston Terrier-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Dachshund Mix</td>
            <td>Boston Terrier-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Danish-Swedish Farmdog Mix</td>
            <td>Boston Terrier-Danish-Swedish Farmdog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Doberman Pinscher Mix</td>
            <td>Boston Terrier-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-French Bulldog Mix</td>
            <td>Boston Terrier-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Labrador Retriever Mix</td>
            <td>Boston Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pomeranian Mix</td>
            <td>Boston Terrier-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Pug Mix</td>
            <td>Boston Terrier-Pug Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Rat Terrier Mix</td>
            <td>Boston Terrier-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Boston Terrier-Russell Terrier Mix</td>
            <td>Boston Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres</td>
            <td>Bouvier des Flandres</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Airedale Terrier Mix</td>
            <td>Bouvier des Flandres-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Bouvier des Flandres-Standard Poodle Mix</td>
            <td>Bouvier des Flandres-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Boxer</td>
            <td>Boxer</td>
        </tr>
        <tr>
            <td>-Boxer Mix</td>
            <td>Boxer Mix</td>
        </tr>
        <tr>
            <td>Boxer- Mix</td>
            <td>Boxer- Mix</td>
        </tr>
        <tr>
            <td>Boxer-Akita Mix</td>
            <td>Boxer-Akita Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Foxhound Mix</td>
            <td>Boxer-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Pit Bull Terrier Mix</td>
            <td>Boxer-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-American Staffordshire Terrier Mix</td>
            <td>Boxer-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Cattle Dog Mix</td>
            <td>Boxer-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Australian Shepherd Mix</td>
            <td>Boxer-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bloodhound Mix</td>
            <td>Boxer-Bloodhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Border Collie Mix</td>
            <td>Boxer-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Boxer-Boston Terrier Mix</td>
            <td>Boxer-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bull Terrier Mix</td>
            <td>Boxer-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bulldog Mix</td>
            <td>Boxer-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Bullmastiff Mix</td>
            <td>Boxer-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Cocker Spaniel Mix</td>
            <td>Boxer-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dachshund Mix</td>
            <td>Boxer-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dalmatian Mix</td>
            <td>Boxer-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Boxer-Doberman Pinscher Mix</td>
            <td>Boxer-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Boxer-Dutch Shepherd Mix</td>
            <td>Boxer-Dutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Foxhound Mix</td>
            <td>Boxer-English Foxhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-English Springer Spaniel Mix</td>
            <td>Boxer-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boxer-German Shepherd Dog Mix</td>
            <td>Boxer-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Boxer-Golden Retriever Mix</td>
            <td>Boxer-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Dane Mix</td>
            <td>Boxer-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Boxer-Great Pyrenees Mix</td>
            <td>Boxer-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Boxer-Greyhound Mix</td>
            <td>Boxer-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Ibizan Hound Mix</td>
            <td>Boxer-Ibizan Hound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Jindo Mix</td>
            <td>Boxer-Jindo Mix</td>
        </tr>
        <tr>
            <td>Boxer-Labrador Retriever Mix</td>
            <td>Boxer-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Boxer-Manchester Terrier Mix</td>
            <td>Boxer-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Mastiff Mix</td>
            <td>Boxer-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Boxer-Poodle Mix</td>
            <td>Boxer-Poodle Mix</td>
        </tr>
        <tr>
            <td>Boxer-Pug Mix</td>
            <td>Boxer-Pug Mix</td>
        </tr>
        <tr>
            <td>Boxer-Redbone Coonhound Mix</td>
            <td>Boxer-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rhodesian Ridgeback Mix</td>
            <td>Boxer-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Boxer-Rottweiler Mix</td>
            <td>Boxer-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Boxer-Russell Terrier Mix</td>
            <td>Boxer-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Siberian Husky Mix</td>
            <td>Boxer-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Boxer-St. Bernard Mix</td>
            <td>Boxer-St. Bernard Mix</td>
        </tr>
        <tr>
            <td>Boxer-Staffordshire Bull Terrier Mix</td>
            <td>Boxer-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Boxer-Treeing Walker Coonhound Mix</td>
            <td>Boxer-Treeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>Boxer-Vizsla Mix</td>
            <td>Boxer-Vizsla Mix</td>
        </tr>
        <tr>
            <td>Boxer-Weimaraner Mix</td>
            <td>Boxer-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel</td>
            <td>Boykin Spaniel</td>
        </tr>
        <tr>
            <td>Boykin Spaniel- Mix</td>
            <td>Boykin Spaniel- Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Deutscher Wachtelhund Mix</td>
            <td>Boykin Spaniel-Deutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-English Cocker Spaniel Mix</td>
            <td>Boykin Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Boykin Spaniel-Irish Setter Mix</td>
            <td>Boykin Spaniel-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Braque du Bourbonnais</td>
            <td>Braque du Bourbonnais</td>
        </tr>
        <tr>
            <td>Briard</td>
            <td>Briard</td>
        </tr>
        <tr>
            <td>Brittany</td>
            <td>Brittany</td>
        </tr>
        <tr>
            <td>Brittany-Basset Hound Mix</td>
            <td>Brittany-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Brittany-Border Collie Mix</td>
            <td>Brittany-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Brittany-English Springer Spaniel Mix</td>
            <td>Brittany-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shepherd Dog Mix</td>
            <td>Brittany-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Brittany-German Shorthaired Pointer Mix</td>
            <td>Brittany-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Golden Retriever Mix</td>
            <td>Brittany-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Irish Setter Mix</td>
            <td>Brittany-Irish Setter Mix</td>
        </tr>
        <tr>
            <td>Brittany-Labrador Retriever Mix</td>
            <td>Brittany-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pekingese Mix</td>
            <td>Brittany-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Brittany-Pointer Mix</td>
            <td>Brittany-Pointer Mix</td>
        </tr>
        <tr>
            <td>Brittany-Poodle Mix</td>
            <td>Brittany-Poodle Mix</td>
        </tr>
        <tr>
            <td>Brittany-Siberian Husky Mix</td>
            <td>Brittany-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon</td>
            <td>Brussels Griffon</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Border Terrier Mix</td>
            <td>Brussels Griffon-Border Terrier Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Poodle Mix</td>
            <td>Brussels Griffon-Poodle Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Pug Mix</td>
            <td>Brussels Griffon-Pug Mix</td>
        </tr>
        <tr>
            <td>Brussels Griffon-Shih Tzu Mix</td>
            <td>Brussels Griffon-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Bugg</td>
            <td>Bugg</td>
        </tr>
        <tr>
            <td>Bull Terrier</td>
            <td>Bull Terrier</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Foxhound Mix</td>
            <td>Bull Terrier-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-American Staffordshire Terrier Mix</td>
            <td>Bull Terrier-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Boxer Mix</td>
            <td>Bull Terrier-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Labrador Retriever Mix</td>
            <td>Bull Terrier-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Staffordshire Bull Terrier Mix</td>
            <td>Bull Terrier-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bull Terrier-Whippet Mix</td>
            <td>Bull Terrier-Whippet Mix</td>
        </tr>
        <tr>
            <td>BullBoxer</td>
            <td>BullBoxer</td>
        </tr>
        <tr>
            <td>Bulldog</td>
            <td>Bulldog</td>
        </tr>
        <tr>
            <td>Bulldog-American Pit Bull Terrier Mix</td>
            <td>Bulldog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-American Staffordshire Terrier Mix</td>
            <td>Bulldog-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Basset Hound Mix</td>
            <td>Bulldog-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Beagle Mix</td>
            <td>Bulldog-Beagle Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boston Terrier Mix</td>
            <td>Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Boxer Mix</td>
            <td>Bulldog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Bullmastiff Mix</td>
            <td>Bulldog-Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Chesapeake Bay Retriever Mix</td>
            <td>Bulldog-Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Cocker Spaniel Mix</td>
            <td>Bulldog-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Dogo Argentino Mix</td>
            <td>Bulldog-Dogo Argentino Mix</td>
        </tr>
        <tr>
            <td>Bulldog-French Bulldog Mix</td>
            <td>Bulldog-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shepherd Dog Mix</td>
            <td>Bulldog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bulldog-German Shorthaired Pointer Mix</td>
            <td>Bulldog-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Great Dane Mix</td>
            <td>Bulldog-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Labrador Retriever Mix</td>
            <td>Bulldog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Mastiff Mix</td>
            <td>Bulldog-Mastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Neapolitan Mastiff Mix</td>
            <td>Bulldog-Neapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Pug Mix</td>
            <td>Bulldog-Pug Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rhodesian Ridgeback Mix</td>
            <td>Bulldog-Rhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Rottweiler Mix</td>
            <td>Bulldog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Bulldog-Wirehaired Pointing Griffon Mix</td>
            <td>Bulldog-Wirehaired Pointing Griffon Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff</td>
            <td>Bullmastiff</td>
        </tr>
        <tr>
            <td>Bullmastiff- Mix</td>
            <td>Bullmastiff- Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Pit Bull Terrier Mix</td>
            <td>Bullmastiff-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-American Staffordshire Terrier Mix</td>
            <td>Bullmastiff-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Border Collie Mix</td>
            <td>Bullmastiff-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Boxer Mix</td>
            <td>Bullmastiff-Boxer Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bull Terrier Mix</td>
            <td>Bullmastiff-Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Bulldog Mix</td>
            <td>Bullmastiff-Bulldog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Chinese Shar-Pei Mix</td>
            <td>Bullmastiff-Chinese Shar-Pei Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Dogue de Bordeaux Mix</td>
            <td>Bullmastiff-Dogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-German Shepherd Dog Mix</td>
            <td>Bullmastiff-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Labrador Retriever Mix</td>
            <td>Bullmastiff-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Redbone Coonhound Mix</td>
            <td>Bullmastiff-Redbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>Bullmastiff-Staffordshire Bull Terrier Mix</td>
            <td>Bullmastiff-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier</td>
            <td>Cairn Terrier</td>
        </tr>
        <tr>
            <td>-Cairn Terrier Mix</td>
            <td>Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Airedale Terrier Mix</td>
            <td>Cairn Terrier-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Australian Terrier Mix</td>
            <td>Cairn Terrier-Australian Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Cocker Spaniel Mix</td>
            <td>Cairn Terrier-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-German Shepherd Dog Mix</td>
            <td>Cairn Terrier-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Jack Russell Terrier Mix</td>
            <td>Cairn Terrier-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Lhasa Apso Mix</td>
            <td>Cairn Terrier-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Pomeranian Mix</td>
            <td>Cairn Terrier-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Poodle Mix</td>
            <td>Cairn Terrier-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Russell Terrier Mix</td>
            <td>Cairn Terrier-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Shih Tzu Mix</td>
            <td>Cairn Terrier-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Smooth Fox Terrier Mix</td>
            <td>Cairn Terrier-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-West Highland White Terrier Mix</td>
            <td>Cairn Terrier-West Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>Cairn Terrier-Yorkshire Terrier Mix</td>
            <td>Cairn Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Canaan Dog</td>
            <td>Canaan Dog</td>
        </tr>
        <tr>
            <td>Canaan Dog- Mix</td>
            <td>Canaan Dog- Mix</td>
        </tr>
        <tr>
            <td>Cane Corso</td>
            <td>Cane Corso</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi</td>
            <td>Cardigan Welsh Corgi</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Eskimo Dog Mix</td>
            <td>Cardigan Welsh Corgi-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Pit Bull Terrier Mix</td>
            <td>Cardigan Welsh Corgi-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-American Staffordshire Terrier Mix</td>
            <td>Cardigan Welsh Corgi-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Cattle Dog Mix</td>
            <td>Cardigan Welsh Corgi-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Australian Shepherd Mix</td>
            <td>Cardigan Welsh Corgi-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Beagle Mix</td>
            <td>Cardigan Welsh Corgi-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Cairn Terrier Mix</td>
            <td>Cardigan Welsh Corgi-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Catahoula Leopard Dog Mix</td>
            <td>Cardigan Welsh Corgi-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-German Shepherd Dog Mix</td>
            <td>Cardigan Welsh Corgi-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Labrador Retriever Mix</td>
            <td>Cardigan Welsh Corgi-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Lancashire Heeler Mix</td>
            <td>Cardigan Welsh Corgi-Lancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Pomeranian Mix</td>
            <td>Cardigan Welsh Corgi-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Russell Terrier Mix</td>
            <td>Cardigan Welsh Corgi-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Cardigan Welsh Corgi-Yorkshire Terrier Mix</td>
            <td>Cardigan Welsh Corgi-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog</td>
            <td>Catahoula Leopard Dog</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog- Mix</td>
            <td>Catahoula Leopard Dog- Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Leopard Hound Mix</td>
            <td>Catahoula Leopard Dog-American Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-American Pit Bull Terrier Mix</td>
            <td>Catahoula Leopard Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Cattle Dog Mix</td>
            <td>Catahoula Leopard Dog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Australian Shepherd Mix</td>
            <td>Catahoula Leopard Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Bluetick Coonhound Mix</td>
            <td>Catahoula Leopard Dog-Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Border Collie Mix</td>
            <td>Catahoula Leopard Dog-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Boxer Mix</td>
            <td>Catahoula Leopard Dog-Boxer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-German Shepherd Dog Mix</td>
            <td>Catahoula Leopard Dog-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Labrador Retriever Mix</td>
            <td>Catahoula Leopard Dog-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Plott Mix</td>
            <td>Catahoula Leopard Dog-Plott Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Pointer Mix</td>
            <td>Catahoula Leopard Dog-Pointer Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Rottweiler Mix</td>
            <td>Catahoula Leopard Dog-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Shetland Sheepdog Mix</td>
            <td>Catahoula Leopard Dog-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Catahoula Leopard Dog-Siberian Husky Mix</td>
            <td>Catahoula Leopard Dog-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Caucasian Ovcharka</td>
            <td>Caucasian Ovcharka</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel</td>
            <td>Cavalier King Charles Spaniel</td>
        </tr>
        <tr>
            <td>-Cavalier King Charles Spaniel Mix</td>
            <td>Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Australian Shepherd Mix</td>
            <td>Cavalier King Charles Spaniel-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Beagle Mix</td>
            <td>Cavalier King Charles Spaniel-Beagle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Bichon Frise Mix</td>
            <td>Cavalier King Charles Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Cocker Spaniel Mix</td>
            <td>Cavalier King Charles Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Coton de Tulear Mix</td>
            <td>Cavalier King Charles Spaniel-Coton de Tulear Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-English Springer Spaniel Mix</td>
            <td>Cavalier King Charles Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Maltese Mix</td>
            <td>Cavalier King Charles Spaniel-Maltese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Papillon Mix</td>
            <td>Cavalier King Charles Spaniel-Papillon Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pekingese Mix</td>
            <td>Cavalier King Charles Spaniel-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Pomeranian Mix</td>
            <td>Cavalier King Charles Spaniel-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Poodle Mix</td>
            <td>Cavalier King Charles Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Shih Tzu Mix</td>
            <td>Cavalier King Charles Spaniel-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cavalier King Charles Spaniel-Standard Poodle Mix</td>
            <td>Cavalier King Charles Spaniel-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog</td>
            <td>Central Asian Shepherd Dog</td>
        </tr>
        <tr>
            <td>Central Asian Shepherd Dog-Golden Retriever Mix</td>
            <td>Central Asian Shepherd Dog-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cesky Terrier</td>
            <td>Cesky Terrier</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever</td>
            <td>Chesapeake Bay Retriever</td>
        </tr>
        <tr>
            <td>-Chesapeake Bay Retriever Mix</td>
            <td>Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-American Staffordshire Terrier Mix</td>
            <td>Chesapeake Bay Retriever-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Beagle Mix</td>
            <td>Chesapeake Bay Retriever-Beagle Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-German Shepherd Dog Mix</td>
            <td>Chesapeake Bay Retriever-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Labrador Retriever Mix</td>
            <td>Chesapeake Bay Retriever-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Shih Tzu Mix</td>
            <td>Chesapeake Bay Retriever-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chesapeake Bay Retriever-Siberian Husky Mix</td>
            <td>Chesapeake Bay Retriever-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>Chihuahua</td>
            <td>Chihuahua</td>
        </tr>
        <tr>
            <td>-Chihuahua Mix</td>
            <td>Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Chihuahua- Mix</td>
            <td>Chihuahua- Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Airedale Terrier Mix</td>
            <td>Chihuahua-Airedale Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Pit Bull Terrier Mix</td>
            <td>Chihuahua-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Staffordshire Terrier Mix</td>
            <td>Chihuahua-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-American Water Spaniel Mix</td>
            <td>Chihuahua-American Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Australian Terrier Mix</td>
            <td>Chihuahua-Australian Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Beagle Mix</td>
            <td>Chihuahua-Beagle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Bichon Frise Mix</td>
            <td>Chihuahua-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Boston Terrier Mix</td>
            <td>Chihuahua-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cairn Terrier Mix</td>
            <td>Chihuahua-Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cardigan Welsh Corgi Mix</td>
            <td>Chihuahua-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Chinese Crested Mix</td>
            <td>Chihuahua-Chinese Crested Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Cocker Spaniel Mix</td>
            <td>Chihuahua-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Dachshund Mix</td>
            <td>Chihuahua-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Doberman Pinscher Mix</td>
            <td>Chihuahua-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Golden Retriever Mix</td>
            <td>Chihuahua-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Italian Greyhound Mix</td>
            <td>Chihuahua-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Jack Russell Terrier Mix</td>
            <td>Chihuahua-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Japanese Chin Mix</td>
            <td>Chihuahua-Japanese Chin Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Labrador Retriever Mix</td>
            <td>Chihuahua-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Lhasa Apso Mix</td>
            <td>Chihuahua-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Maltese Mix</td>
            <td>Chihuahua-Maltese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Manchester Terrier Mix</td>
            <td>Chihuahua-Manchester Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Australian Shepherd Mix</td>
            <td>Chihuahua-Miniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Pinscher Mix</td>
            <td>Chihuahua-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Miniature Schnauzer Mix</td>
            <td>Chihuahua-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Norwich Terrier Mix</td>
            <td>Chihuahua-Norwich Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Papillon Mix</td>
            <td>Chihuahua-Papillon Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Parson Russell Terrier Mix</td>
            <td>Chihuahua-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pekingese Mix</td>
            <td>Chihuahua-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pembroke Welsh Corgi Mix</td>
            <td>Chihuahua-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pomeranian Mix</td>
            <td>Chihuahua-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Poodle Mix</td>
            <td>Chihuahua-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Pug Mix</td>
            <td>Chihuahua-Pug Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Rat Terrier Mix</td>
            <td>Chihuahua-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Russell Terrier Mix</td>
            <td>Chihuahua-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Schipperke Mix</td>
            <td>Chihuahua-Schipperke Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shiba Inu Mix</td>
            <td>Chihuahua-Shiba Inu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Shih Tzu Mix</td>
            <td>Chihuahua-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Smooth Fox Terrier Mix</td>
            <td>Chihuahua-Smooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Toy Fox Terrier Mix</td>
            <td>Chihuahua-Toy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Whippet Mix</td>
            <td>Chihuahua-Whippet Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Wire Fox Terrier Mix</td>
            <td>Chihuahua-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Xoloitzcuintli Mix</td>
            <td>Chihuahua-Xoloitzcuintli Mix</td>
        </tr>
        <tr>
            <td>Chihuahua-Yorkshire Terrier Mix</td>
            <td>Chihuahua-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested</td>
            <td>Chinese Crested</td>
        </tr>
        <tr>
            <td>Chinese Crested-Chihuahua Mix</td>
            <td>Chinese Crested-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Jack Russell Terrier Mix</td>
            <td>Chinese Crested-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Lhasa Apso Mix</td>
            <td>Chinese Crested-Lhasa Apso Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Maltese Mix</td>
            <td>Chinese Crested-Maltese Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Papillon Mix</td>
            <td>Chinese Crested-Papillon Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Poodle Mix</td>
            <td>Chinese Crested-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Pug Mix</td>
            <td>Chinese Crested-Pug Mix</td>
        </tr>
        <tr>
            <td>Chinese Crested-Russell Terrier Mix</td>
            <td>Chinese Crested-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei</td>
            <td>Chinese Shar-Pei</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei- Mix</td>
            <td>Chinese Shar-Pei- Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-American Pit Bull Terrier Mix</td>
            <td>Chinese Shar-Pei-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Australian Cattle Dog Mix</td>
            <td>Chinese Shar-Pei-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Basset Hound Mix</td>
            <td>Chinese Shar-Pei-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Boerboel Mix</td>
            <td>Chinese Shar-Pei-Boerboel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Cocker Spaniel Mix</td>
            <td>Chinese Shar-Pei-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-German Shepherd Dog Mix</td>
            <td>Chinese Shar-Pei-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Great Dane Mix</td>
            <td>Chinese Shar-Pei-Great Dane Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Labrador Retriever Mix</td>
            <td>Chinese Shar-Pei-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Pug Mix</td>
            <td>Chinese Shar-Pei-Pug Mix</td>
        </tr>
        <tr>
            <td>Chinese Shar-Pei-Staffordshire Bull Terrier Mix</td>
            <td>Chinese Shar-Pei-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chinook</td>
            <td>Chinook</td>
        </tr>
        <tr>
            <td>Chinook-German Shepherd Dog Mix</td>
            <td>Chinook-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow</td>
            <td>Chow Chow</td>
        </tr>
        <tr>
            <td>Chow Chow-American Pit Bull Terrier Mix</td>
            <td>Chow Chow-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Australian Shepherd Mix</td>
            <td>Chow Chow-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Catahoula Leopard Dog Mix</td>
            <td>Chow Chow-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Cocker Spaniel Mix</td>
            <td>Chow Chow-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Collie Mix</td>
            <td>Chow Chow-Collie Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-German Shepherd Dog Mix</td>
            <td>Chow Chow-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Golden Retriever Mix</td>
            <td>Chow Chow-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Keeshond Mix</td>
            <td>Chow Chow-Keeshond Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Labrador Retriever Mix</td>
            <td>Chow Chow-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Newfoundland Mix</td>
            <td>Chow Chow-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Norfolk Terrier Mix</td>
            <td>Chow Chow-Norfolk Terrier Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Pembroke Welsh Corgi Mix</td>
            <td>Chow Chow-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Poodle Mix</td>
            <td>Chow Chow-Poodle Mix</td>
        </tr>
        <tr>
            <td>Chow Chow-Rottweiler Mix</td>
            <td>Chow Chow-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Cirneco dell&quot;Etna</td>
            <td>Cirneco dell&quot;Etna</td>
        </tr>
        <tr>
            <td>Clumber Spaniel</td>
            <td>Clumber Spaniel</td>
        </tr>
        <tr>
            <td>Clumber Spaniel-English Springer Spaniel Mix</td>
            <td>Clumber Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cockapoo</td>
            <td>Cockapoo</td>
        </tr>
        <tr>
            <td>Cocker Spaniel</td>
            <td>Cocker Spaniel</td>
        </tr>
        <tr>
            <td>-Cocker Spaniel Mix</td>
            <td>Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Bichon Frise Mix</td>
            <td>Cocker Spaniel-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Boxer Mix</td>
            <td>Cocker Spaniel-Boxer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Cavalier King Charles Spaniel Mix</td>
            <td>Cocker Spaniel-Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Chow Chow Mix</td>
            <td>Cocker Spaniel-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Dachshund Mix</td>
            <td>Cocker Spaniel-Dachshund Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Doberman Pinscher Mix</td>
            <td>Cocker Spaniel-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Cocker Spaniel Mix</td>
            <td>Cocker Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-English Springer Spaniel Mix</td>
            <td>Cocker Spaniel-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Golden Retriever Mix</td>
            <td>Cocker Spaniel-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Labrador Retriever Mix</td>
            <td>Cocker Spaniel-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Maltese Mix</td>
            <td>Cocker Spaniel-Maltese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Pinscher Mix</td>
            <td>Cocker Spaniel-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Miniature Schnauzer Mix</td>
            <td>Cocker Spaniel-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pekingese Mix</td>
            <td>Cocker Spaniel-Pekingese Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pomeranian Mix</td>
            <td>Cocker Spaniel-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Poodle Mix</td>
            <td>Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Pug Mix</td>
            <td>Cocker Spaniel-Pug Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Rat Terrier Mix</td>
            <td>Cocker Spaniel-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shetland Sheepdog Mix</td>
            <td>Cocker Spaniel-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Shih Tzu Mix</td>
            <td>Cocker Spaniel-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Standard Schnauzer Mix</td>
            <td>Cocker Spaniel-Standard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Cocker Spaniel-Tibetan Spaniel Mix</td>
            <td>Cocker Spaniel-Tibetan Spaniel Mix</td>
        </tr>
        <tr>
            <td>Collie</td>
            <td>Collie</td>
        </tr>
        <tr>
            <td>-Collie Mix</td>
            <td>Collie Mix</td>
        </tr>
        <tr>
            <td>Collie- Mix</td>
            <td>Collie- Mix</td>
        </tr>
        <tr>
            <td>Collie-American Foxhound Mix</td>
            <td>Collie-American Foxhound Mix</td>
        </tr>
        <tr>
            <td>Collie-Anatolian Shepherd Dog Mix</td>
            <td>Collie-Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Australian Cattle Dog Mix</td>
            <td>Collie-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-Belgian Malinois Mix</td>
            <td>Collie-Belgian Malinois Mix</td>
        </tr>
        <tr>
            <td>Collie-Boxer Mix</td>
            <td>Collie-Boxer Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shepherd Dog Mix</td>
            <td>Collie-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Collie-German Shorthaired Pointer Mix</td>
            <td>Collie-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Collie-Golden Retriever Mix</td>
            <td>Collie-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Labrador Retriever Mix</td>
            <td>Collie-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Collie-Shetland Sheepdog Mix</td>
            <td>Collie-Shetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear</td>
            <td>Coton de Tulear</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Chow Chow Mix</td>
            <td>Coton de Tulear-Chow Chow Mix</td>
        </tr>
        <tr>
            <td>Coton de Tulear-Poodle Mix</td>
            <td>Coton de Tulear-Poodle Mix</td>
        </tr>
        <tr>
            <td>Curly-Coated Retriever</td>
            <td>Curly-Coated Retriever</td>
        </tr>
        <tr>
            <td>Czechoslovakian Vlcak</td>
            <td>Czechoslovakian Vlcak</td>
        </tr>
        <tr>
            <td>Dachshund</td>
            <td>Dachshund</td>
        </tr>
        <tr>
            <td>Dachshund- Mix</td>
            <td>Dachshund- Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Pit Bull Terrier Mix</td>
            <td>Dachshund-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-American Staffordshire Terrier Mix</td>
            <td>Dachshund-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Basset Hound Mix</td>
            <td>Dachshund-Basset Hound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Beagle Mix</td>
            <td>Dachshund-Beagle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Bichon Frise Mix</td>
            <td>Dachshund-Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Black Russian Terrier Mix</td>
            <td>Dachshund-Black Russian Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Boston Terrier Mix</td>
            <td>Dachshund-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cardigan Welsh Corgi Mix</td>
            <td>Dachshund-Cardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Chihuahua Mix</td>
            <td>Dachshund-Chihuahua Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Cocker Spaniel Mix</td>
            <td>Dachshund-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Doberman Pinscher Mix</td>
            <td>Dachshund-Doberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Flat-Coated Retriever Mix</td>
            <td>Dachshund-Flat-Coated Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-French Bulldog Mix</td>
            <td>Dachshund-French Bulldog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Pinscher Mix</td>
            <td>Dachshund-German Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shepherd Dog Mix</td>
            <td>Dachshund-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Dachshund-German Shorthaired Pointer Mix</td>
            <td>Dachshund-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Glen of Imaal Terrier Mix</td>
            <td>Dachshund-Glen of Imaal Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Golden Retriever Mix</td>
            <td>Dachshund-Golden Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Italian Greyhound Mix</td>
            <td>Dachshund-Italian Greyhound Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Jack Russell Terrier Mix</td>
            <td>Dachshund-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Labrador Retriever Mix</td>
            <td>Dachshund-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Maltese Mix</td>
            <td>Dachshund-Maltese Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Pinscher Mix</td>
            <td>Dachshund-Miniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Miniature Schnauzer Mix</td>
            <td>Dachshund-Miniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Parson Russell Terrier Mix</td>
            <td>Dachshund-Parson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pembroke Welsh Corgi Mix</td>
            <td>Dachshund-Pembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pomeranian Mix</td>
            <td>Dachshund-Pomeranian Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Poodle Mix</td>
            <td>Dachshund-Poodle Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Pug Mix</td>
            <td>Dachshund-Pug Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Rat Terrier Mix</td>
            <td>Dachshund-Rat Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Russell Terrier Mix</td>
            <td>Dachshund-Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Scottish Terrier Mix</td>
            <td>Dachshund-Scottish Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Shih Tzu Mix</td>
            <td>Dachshund-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Staffordshire Bull Terrier Mix</td>
            <td>Dachshund-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Wire Fox Terrier Mix</td>
            <td>Dachshund-Wire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>Dachshund-Yorkshire Terrier Mix</td>
            <td>Dachshund-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian</td>
            <td>Dalmatian</td>
        </tr>
        <tr>
            <td>Dalmatian-American Pit Bull Terrier Mix</td>
            <td>Dalmatian-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Cattle Dog Mix</td>
            <td>Dalmatian-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Australian Shepherd Mix</td>
            <td>Dalmatian-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Beagle Mix</td>
            <td>Dalmatian-Beagle Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Border Collie Mix</td>
            <td>Dalmatian-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Great Pyrenees Mix</td>
            <td>Dalmatian-Great Pyrenees Mix</td>
        </tr>
        <tr>
            <td>Dalmatian-Labrador Retriever Mix</td>
            <td>Dalmatian-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier</td>
            <td>Dandie Dinmont Terrier</td>
        </tr>
        <tr>
            <td>Dandie Dinmont Terrier-Yorkshire Terrier Mix</td>
            <td>Dandie Dinmont Terrier-Yorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog</td>
            <td>Danish-Swedish Farmdog</td>
        </tr>
        <tr>
            <td>Danish-Swedish Farmdog-Czechoslovakian Vlcak Mix</td>
            <td>Danish-Swedish Farmdog-Czechoslovakian Vlcak Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund</td>
            <td>Deutscher Wachtelhund</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund- Mix</td>
            <td>Deutscher Wachtelhund- Mix</td>
        </tr>
        <tr>
            <td>Deutscher Wachtelhund-Newfoundland Mix</td>
            <td>Deutscher Wachtelhund-Newfoundland Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher</td>
            <td>Doberman Pinscher</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-American Staffordshire Terrier Mix</td>
            <td>Doberman Pinscher-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beagle Mix</td>
            <td>Doberman Pinscher-Beagle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Beauceron Mix</td>
            <td>Doberman Pinscher-Beauceron Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Black and Tan Coonhound Mix</td>
            <td>Doberman Pinscher-Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Boxer Mix</td>
            <td>Doberman Pinscher-Boxer Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Catahoula Leopard Dog Mix</td>
            <td>Doberman Pinscher-Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Dalmatian Mix</td>
            <td>Doberman Pinscher-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-German Shepherd Dog Mix</td>
            <td>Doberman Pinscher-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Greyhound Mix</td>
            <td>Doberman Pinscher-Greyhound Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Labrador Retriever Mix</td>
            <td>Doberman Pinscher-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Poodle Mix</td>
            <td>Doberman Pinscher-Poodle Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Pug Mix</td>
            <td>Doberman Pinscher-Pug Mix</td>
        </tr>
        <tr>
            <td>Doberman Pinscher-Rottweiler Mix</td>
            <td>Doberman Pinscher-Rottweiler Mix</td>
        </tr>
        <tr>
            <td>Dogo Argentino</td>
            <td>Dogo Argentino</td>
        </tr>
        <tr>
            <td>Dogo Argentino-American Pit Bull Terrier Mix</td>
            <td>Dogo Argentino-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux</td>
            <td>Dogue de Bordeaux</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-American Pit Bull Terrier Mix</td>
            <td>Dogue de Bordeaux-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Boxer Mix</td>
            <td>Dogue de Bordeaux-Boxer Mix</td>
        </tr>
        <tr>
            <td>Dogue de Bordeaux-Labrador Retriever Mix</td>
            <td>Dogue de Bordeaux-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Drentsche Patrijshond</td>
            <td>Drentsche Patrijshond</td>
        </tr>
        <tr>
            <td>Dutch Shepherd</td>
            <td>Dutch Shepherd</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Appenzeller Sennenhunde Mix</td>
            <td>Dutch Shepherd-Appenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Labrador Retriever Mix</td>
            <td>Dutch Shepherd-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Dutch Shepherd-Siberian Husky Mix</td>
            <td>Dutch Shepherd-Siberian Husky Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel</td>
            <td>English Cocker Spaniel</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Cocker Spaniel Mix</td>
            <td>English Cocker Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Cocker Spaniel-Poodle Mix</td>
            <td>English Cocker Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Foxhound</td>
            <td>English Foxhound</td>
        </tr>
        <tr>
            <td>English Foxhound-Labrador Retriever Mix</td>
            <td>English Foxhound-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter</td>
            <td>English Setter</td>
        </tr>
        <tr>
            <td>English Setter- Mix</td>
            <td>English Setter- Mix</td>
        </tr>
        <tr>
            <td>English Setter-Beagle Mix</td>
            <td>English Setter-Beagle Mix</td>
        </tr>
        <tr>
            <td>English Setter-Border Collie Mix</td>
            <td>English Setter-Border Collie Mix</td>
        </tr>
        <tr>
            <td>English Setter-Brittany Mix</td>
            <td>English Setter-Brittany Mix</td>
        </tr>
        <tr>
            <td>English Setter-Dalmatian Mix</td>
            <td>English Setter-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>English Setter-English Springer Spaniel Mix</td>
            <td>English Setter-English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Setter-Labrador Retriever Mix</td>
            <td>English Setter-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Setter-Pointer Mix</td>
            <td>English Setter-Pointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel</td>
            <td>English Springer Spaniel</td>
        </tr>
        <tr>
            <td>English Springer Spaniel- Mix</td>
            <td>English Springer Spaniel- Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Australian Cattle Dog Mix</td>
            <td>English Springer Spaniel-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Border Collie Mix</td>
            <td>English Springer Spaniel-Border Collie Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Cocker Spaniel Mix</td>
            <td>English Springer Spaniel-Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Dalmatian Mix</td>
            <td>English Springer Spaniel-Dalmatian Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-English Cocker Spaniel Mix</td>
            <td>English Springer Spaniel-English Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-German Shepherd Dog Mix</td>
            <td>English Springer Spaniel-German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Jack Russell Terrier Mix</td>
            <td>English Springer Spaniel-Jack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Labrador Retriever Mix</td>
            <td>English Springer Spaniel-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Pointer Mix</td>
            <td>English Springer Spaniel-Pointer Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Poodle Mix</td>
            <td>English Springer Spaniel-Poodle Mix</td>
        </tr>
        <tr>
            <td>English Springer Spaniel-Standard Poodle Mix</td>
            <td>English Springer Spaniel-Standard Poodle Mix</td>
        </tr>
        <tr>
            <td>English Toy Spaniel</td>
            <td>English Toy Spaniel</td>
        </tr>
        <tr>
            <td>Entlebucher Mountain Dog</td>
            <td>Entlebucher Mountain Dog</td>
        </tr>
        <tr>
            <td>Estrela Mountain Dog</td>
            <td>Estrela Mountain Dog</td>
        </tr>
        <tr>
            <td>Eurasier</td>
            <td>Eurasier</td>
        </tr>
        <tr>
            <td>Field Spaniel</td>
            <td>Field Spaniel</td>
        </tr>
        <tr>
            <td>Finnish Lapphund</td>
            <td>Finnish Lapphund</td>
        </tr>
        <tr>
            <td>Finnish Spitz</td>
            <td>Finnish Spitz</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever</td>
            <td>Flat-Coated Retriever</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever- Mix</td>
            <td>Flat-Coated Retriever- Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Border Collie Mix</td>
            <td>Flat-Coated Retriever-Border Collie Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Irish Water Spaniel Mix</td>
            <td>Flat-Coated Retriever-Irish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Labrador Retriever Mix</td>
            <td>Flat-Coated Retriever-Labrador Retriever Mix</td>
        </tr>
        <tr>
            <td>Flat-Coated Retriever-Portuguese Water Dog Mix</td>
            <td>Flat-Coated Retriever-Portuguese Water Dog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog</td>
            <td>French Bulldog</td>
        </tr>
        <tr>
            <td>French Bulldog-Boston Terrier Mix</td>
            <td>French Bulldog-Boston Terrier Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Bulldog Mix</td>
            <td>French Bulldog-Bulldog Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Havanese Mix</td>
            <td>French Bulldog-Havanese Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Pug Mix</td>
            <td>French Bulldog-Pug Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Shih Tzu Mix</td>
            <td>French Bulldog-Shih Tzu Mix</td>
        </tr>
        <tr>
            <td>French Bulldog-Staffordshire Bull Terrier Mix</td>
            <td>French Bulldog-Staffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>French Spaniel</td>
            <td>French Spaniel</td>
        </tr>
        <tr>
            <td>French Spaniel-German Shorthaired Pointer Mix</td>
            <td>French Spaniel-German Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer</td>
            <td>German Longhaired Pointer</td>
        </tr>
        <tr>
            <td>German Longhaired Pointer-Pointer Mix</td>
            <td>German Longhaired Pointer-Pointer Mix</td>
        </tr>
        <tr>
            <td>German Pinscher</td>
            <td>German Pinscher</td>
        </tr>
        <tr>
            <td>German Pinscher-Weimaraner Mix</td>
            <td>German Pinscher-Weimaraner Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog</td>
            <td>German Shepherd Dog</td>
        </tr>
        <tr>
            <td>-German Shepherd Dog Mix</td>
            <td>German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog- Mix</td>
            <td>German Shepherd Dog- Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Akita Mix</td>
            <td>German Shepherd Dog-Akita Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Alaskan Malamute Mix</td>
            <td>German Shepherd Dog-Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Eskimo Dog Mix</td>
            <td>German Shepherd Dog-American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Pit Bull Terrier Mix</td>
            <td>German Shepherd Dog-American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-American Staffordshire Terrier Mix</td>
            <td>German Shepherd Dog-American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Cattle Dog Mix</td>
            <td>German Shepherd Dog-Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Kelpie Mix</td>
            <td>German Shepherd Dog-Australian Kelpie Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Australian Shepherd Mix</td>
            <td>German Shepherd Dog-Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Basenji Mix</td>
            <td>German Shepherd Dog-Basenji Mix</td>
        </tr>
        <tr>
            <td>German Shepherd Dog-Basset Hound Mix</td>
            <td>German Shepherd Dog-Basset Hound Mix</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">2006 rows, truncated to displaylimit of 1000</span>



That certainly gets us a lot closer to the list we might want, but there
are still some entries in the breed\_fixed column that are conceptual
duplicates of each other, due to poor consistency in how the breed names
were entered. For example, one entry is "Beagle Mix" while another is
"Beagle- Mix". These entries are clearly meant to refer to the same
breed, but they will be counted as separate breeds as long as their
breed names are different.

Cleaning up all of the entries in the breed column would take quite a
bit of work, so we won't go through more details about how to do it in
this lesson. Instead, use this exercise as a reminder for why it's so
important to always look at the details of your data, and as motivation
to explore the MySQL functions we won't have time to discuss in the
course. If you push yourself to learn new SQL functions and embrace the
habit of getting to know your data by exploring its raw values and
outputs, you will find that SQL provides very efficient tools to clean
real-world messy data sets, and you will arrive at the correct
conclusions about what your data indicate your company should do.

Now it's time to practice using AS, DISTINCT, and ORDER BY in your own queries.
-------------------------------------------------------------------------------

**Question 4: How would you get a list of all the subcategories of
Dognition tests, in alphabetical order, with no test listed more than
once (if you do not limit your output, you should retrieve 16 rows)?**

.. code:: ipython3

    %%sql
    SELECT DISTINCT subcategory_name 
    FROM complete_tests
    ORDER BY subcategory_name DESC;


.. parsed-literal::

    16 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>subcategory_name</th>
        </tr>
        <tr>
            <td>Spatial Navigation</td>
        </tr>
        <tr>
            <td>Social Bias</td>
        </tr>
        <tr>
            <td>Smell Game</td>
        </tr>
        <tr>
            <td>Shell Game</td>
        </tr>
        <tr>
            <td>Shaker Game</td>
        </tr>
        <tr>
            <td>Self Control Game</td>
        </tr>
        <tr>
            <td>Reasoning</td>
        </tr>
        <tr>
            <td>Perspective Game</td>
        </tr>
        <tr>
            <td>Numerosity</td>
        </tr>
        <tr>
            <td>Memory</td>
        </tr>
        <tr>
            <td>Laterality</td>
        </tr>
        <tr>
            <td>Impossible Task</td>
        </tr>
        <tr>
            <td>Expression Game</td>
        </tr>
        <tr>
            <td>Empathy</td>
        </tr>
        <tr>
            <td>Cunning</td>
        </tr>
        <tr>
            <td>Communication</td>
        </tr>
    </table>



**Question 5: How would you create a text file with a list of all the
non-United States countries of Dognition customers with no country
listed more than once?**

.. code:: ipython3

    non_US_states = %sql SELECT DISTINCT country FROM users WHERE country != 'US';
    non_US_states.csv('non_US_states.csv')  


.. parsed-literal::

    68 rows affected.




.. raw:: html

    <a href="./files/non_US_states.csv">CSV results</a>



**Question 6: How would you find the User ID, Dog ID, and test name of
the first 10 tests to ever be completed in the Dognition database?**

.. code:: ipython3

    %%sql
    SELECT user_guid, dog_guid, test_name
    FROM complete_tests
    ORDER BY created_at
    LIMIT 10;


.. parsed-literal::

    10 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>user_guid</th>
            <th>dog_guid</th>
            <th>test_name</th>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Yawn Warm-up</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Yawn Game</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Eye Contact Warm-up</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Eye Contact Game</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Treat Warm-up</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Arm Pointing</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Foot Pointing</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Watching</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Turn Your Back</td>
        </tr>
        <tr>
            <td>None</td>
            <td>fd27b86c-7144-11e5-ba71-058fbc01cf0b</td>
            <td>Cover Your Eyes</td>
        </tr>
    </table>



**Question 7: How would create a text file with a list of all the
customers with yearly memberships who live in the state of North
Carolina (USA) and joined Dognition after March 1, 2014, sorted so that
the most recent member is at the top of the list?**

.. code:: ipython3

    yearly_memberships = %sql SELECT DISTINCT user_guid, state, created_at FROM users WHERE membership_type=2 AND state="NC" AND created_at>'2014-04-1' ORDER BY created_at DESC;
    yearly_memberships.csv('yearly_memberships.csv')


.. parsed-literal::

    67 rows affected.




.. raw:: html

    <a href="./files/yearly_memberships.csv">CSV results</a>




**Question 8: See if you can find an SQL function from the list provided
at:**

http://www.w3resource.com/mysql/mysql-functions-and-operators.php

**that would allow you to output all of the distinct breed names in
UPPER case. Create a query that would output a list of these names in
upper case, sorted in alphabetical order.**

.. code:: ipython3

    %%sql
    SELECT DISTINCT UPPER(breed), REPLACE(breed,'-','') AS breed_fixed
    FROM dogs
    ORDER BY breed_fixed;


.. parsed-literal::

    2006 rows affected.




.. raw:: html

    <table>
        <tr>
            <th>UPPER(breed)</th>
            <th>breed_fixed</th>
        </tr>
        <tr>
            <td>AFFENPINSCHER</td>
            <td>Affenpinscher</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-AFGHAN HOUND MIX</td>
            <td>AffenpinscherAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-AIREDALE TERRIER MIX</td>
            <td>AffenpinscherAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-ALASKAN MALAMUTE MIX</td>
            <td>AffenpinscherAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-AMERICAN ENGLISH COONHOUND MIX</td>
            <td>AffenpinscherAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-BRUSSELS GRIFFON MIX</td>
            <td>AffenpinscherBrussels Griffon Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-POODLE MIX</td>
            <td>AffenpinscherPoodle Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-RAT TERRIER MIX</td>
            <td>AffenpinscherRat Terrier Mix</td>
        </tr>
        <tr>
            <td>AFFENPINSCHER-SPANISH WATER DOG MIX</td>
            <td>AffenpinscherSpanish Water Dog Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND</td>
            <td>Afghan Hound</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-AFFENPINSCHER MIX</td>
            <td>Afghan HoundAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-AIREDALE TERRIER MIX</td>
            <td>Afghan HoundAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-AKITA MIX</td>
            <td>Afghan HoundAkita Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-BLOODHOUND MIX</td>
            <td>Afghan HoundBloodhound Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-BORDER COLLIE MIX</td>
            <td>Afghan HoundBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AFGHAN HOUND-GOLDEN RETRIEVER MIX</td>
            <td>Afghan HoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER</td>
            <td>Airedale Terrier</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-AFGHAN HOUND MIX</td>
            <td>Airedale TerrierAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-BORDER COLLIE MIX</td>
            <td>Airedale TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-CATAHOULA LEOPARD DOG MIX</td>
            <td>Airedale TerrierCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-GERMAN SHEPHERD DOG MIX</td>
            <td>Airedale TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>Airedale TerrierGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-GOLDEN RETRIEVER MIX</td>
            <td>Airedale TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-LABRADOR RETRIEVER MIX</td>
            <td>Airedale TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AIREDALE TERRIER-PORTUGUESE PODENGO PEQUENO MIX</td>
            <td>Airedale TerrierPortuguese Podengo Pequeno Mix</td>
        </tr>
        <tr>
            <td>AKITA</td>
            <td>Akita</td>
        </tr>
        <tr>
            <td>AKITA- MIX</td>
            <td>Akita Mix</td>
        </tr>
        <tr>
            <td>AKITA-AFFENPINSCHER MIX</td>
            <td>AkitaAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>AKITA-AFGHAN HOUND MIX</td>
            <td>AkitaAfghan Hound Mix</td>
        </tr>
        <tr>
            <td>AKITA-AIREDALE TERRIER MIX</td>
            <td>AkitaAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>AKITA-AMERICAN PIT BULL TERRIER MIX</td>
            <td>AkitaAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AKITA-BEARDED COLLIE MIX</td>
            <td>AkitaBearded Collie Mix</td>
        </tr>
        <tr>
            <td>AKITA-BELGIAN TERVUREN MIX</td>
            <td>AkitaBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>AKITA-BERNESE MOUNTAIN DOG MIX</td>
            <td>AkitaBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>AKITA-GERMAN SHEPHERD DOG MIX</td>
            <td>AkitaGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AKITA-LABRADOR RETRIEVER MIX</td>
            <td>AkitaLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AKITA-SIBERIAN HUSKY MIX</td>
            <td>AkitaSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE</td>
            <td>Alaskan Malamute</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE- MIX</td>
            <td>Alaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Alaskan MalamuteAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-AUSTRALIAN KELPIE MIX</td>
            <td>Alaskan MalamuteAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-BEAGLE MIX</td>
            <td>Alaskan MalamuteBeagle Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-BERNESE MOUNTAIN DOG MIX</td>
            <td>Alaskan MalamuteBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-BORDER COLLIE MIX</td>
            <td>Alaskan MalamuteBorder Collie Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-COLLIE MIX</td>
            <td>Alaskan MalamuteCollie Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-ENGLISH COCKER SPANIEL MIX</td>
            <td>Alaskan MalamuteEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-GERMAN SHEPHERD DOG MIX</td>
            <td>Alaskan MalamuteGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-LABRADOR RETRIEVER MIX</td>
            <td>Alaskan MalamuteLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-POMERANIAN MIX</td>
            <td>Alaskan MalamutePomeranian Mix</td>
        </tr>
        <tr>
            <td>ALASKAN MALAMUTE-SIBERIAN HUSKY MIX</td>
            <td>Alaskan MalamuteSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ENGLISH COONHOUND</td>
            <td>American English Coonhound</td>
        </tr>
        <tr>
            <td>AMERICAN ENGLISH COONHOUND-GOLDEN RETRIEVER MIX</td>
            <td>American English CoonhoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ENGLISH COONHOUND-REDBONE COONHOUND MIX</td>
            <td>American English CoonhoundRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ENGLISH COONHOUND-RHODESIAN RIDGEBACK MIX</td>
            <td>American English CoonhoundRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ENGLISH COONHOUND-WEIMARANER MIX</td>
            <td>American English CoonhoundWeimaraner Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG</td>
            <td>American Eskimo Dog</td>
        </tr>
        <tr>
            <td>-AMERICAN ESKIMO DOG MIX</td>
            <td>American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG- MIX</td>
            <td>American Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-AUSTRALIAN SHEPHERD MIX</td>
            <td>American Eskimo DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-BORDER COLLIE MIX</td>
            <td>American Eskimo DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-CHIHUAHUA MIX</td>
            <td>American Eskimo DogChihuahua Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-COCKER SPANIEL MIX</td>
            <td>American Eskimo DogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-COLLIE MIX</td>
            <td>American Eskimo DogCollie Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>American Eskimo DogEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-GOLDEN RETRIEVER MIX</td>
            <td>American Eskimo DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-PAPILLON MIX</td>
            <td>American Eskimo DogPapillon Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-PEMBROKE WELSH CORGI MIX</td>
            <td>American Eskimo DogPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-POMERANIAN MIX</td>
            <td>American Eskimo DogPomeranian Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-POODLE MIX</td>
            <td>American Eskimo DogPoodle Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-RUSSELL TERRIER MIX</td>
            <td>American Eskimo DogRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-SHIBA INU MIX</td>
            <td>American Eskimo DogShiba Inu Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-SIBERIAN HUSKY MIX</td>
            <td>American Eskimo DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>AMERICAN ESKIMO DOG-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>American Eskimo DogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND</td>
            <td>American Foxhound</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND- MIX</td>
            <td>American Foxhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND-ANATOLIAN SHEPHERD DOG MIX</td>
            <td>American FoxhoundAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND-BEAGLE MIX</td>
            <td>American FoxhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND-GERMAN SHEPHERD DOG MIX</td>
            <td>American FoxhoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND-LABRADOR RETRIEVER MIX</td>
            <td>American FoxhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN FOXHOUND-POINTER MIX</td>
            <td>American FoxhoundPointer Mix</td>
        </tr>
        <tr>
            <td>AMERICAN HAIRLESS TERRIER</td>
            <td>American Hairless Terrier</td>
        </tr>
        <tr>
            <td>AMERICAN HAIRLESS TERRIER-SHETLAND SHEEPDOG MIX</td>
            <td>American Hairless TerrierShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN LEOPARD HOUND</td>
            <td>American Leopard Hound</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER</td>
            <td>American Pit Bull Terrier</td>
        </tr>
        <tr>
            <td>-AMERICAN PIT BULL TERRIER MIX</td>
            <td>American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER- MIX</td>
            <td>American Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-AMERICAN ENGLISH COONHOUND MIX</td>
            <td>American Pit Bull TerrierAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-AMERICAN LEOPARD HOUND MIX</td>
            <td>American Pit Bull TerrierAmerican Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>American Pit Bull TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-AUSTRALIAN CATTLE DOG MIX</td>
            <td>American Pit Bull TerrierAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-AUSTRALIAN SHEPHERD MIX</td>
            <td>American Pit Bull TerrierAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BEAGLE MIX</td>
            <td>American Pit Bull TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BORDER COLLIE MIX</td>
            <td>American Pit Bull TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BOSTON TERRIER MIX</td>
            <td>American Pit Bull TerrierBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BOXER MIX</td>
            <td>American Pit Bull TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BRITTANY MIX</td>
            <td>American Pit Bull TerrierBrittany Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BULL TERRIER MIX</td>
            <td>American Pit Bull TerrierBull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BULLDOG MIX</td>
            <td>American Pit Bull TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-BULLMASTIFF MIX</td>
            <td>American Pit Bull TerrierBullmastiff Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-CANE CORSO MIX</td>
            <td>American Pit Bull TerrierCane Corso Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-CARDIGAN WELSH CORGI MIX</td>
            <td>American Pit Bull TerrierCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-CHINESE SHAR-PEI MIX</td>
            <td>American Pit Bull TerrierChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-DOBERMAN PINSCHER MIX</td>
            <td>American Pit Bull TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-DOGUE DE BORDEAUX MIX</td>
            <td>American Pit Bull TerrierDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-GERMAN SHEPHERD DOG MIX</td>
            <td>American Pit Bull TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-GREAT DANE MIX</td>
            <td>American Pit Bull TerrierGreat Dane Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-GREAT PYRENEES MIX</td>
            <td>American Pit Bull TerrierGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-GREYHOUND MIX</td>
            <td>American Pit Bull TerrierGreyhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-LABRADOR RETRIEVER MIX</td>
            <td>American Pit Bull TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-MASTIFF MIX</td>
            <td>American Pit Bull TerrierMastiff Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-PARSON RUSSELL TERRIER MIX</td>
            <td>American Pit Bull TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-PLOTT MIX</td>
            <td>American Pit Bull TerrierPlott Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-POINTER MIX</td>
            <td>American Pit Bull TerrierPointer Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-RHODESIAN RIDGEBACK MIX</td>
            <td>American Pit Bull TerrierRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-ROTTWEILER MIX</td>
            <td>American Pit Bull TerrierRottweiler Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-SIBERIAN HUSKY MIX</td>
            <td>American Pit Bull TerrierSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>American Pit Bull TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-TREEING TENNESSEE BRINDLE MIX</td>
            <td>American Pit Bull TerrierTreeing Tennessee Brindle Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-VIZSLA MIX</td>
            <td>American Pit Bull TerrierVizsla Mix</td>
        </tr>
        <tr>
            <td>AMERICAN PIT BULL TERRIER-WHIPPET MIX</td>
            <td>American Pit Bull TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER</td>
            <td>American Staffordshire Terrier</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER- MIX</td>
            <td>American Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-AIREDALE TERRIER MIX</td>
            <td>American Staffordshire TerrierAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-AMERICAN PIT BULL TERRIER MIX</td>
            <td>American Staffordshire TerrierAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-AUSTRALIAN SHEPHERD MIX</td>
            <td>American Staffordshire TerrierAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BEAGLE MIX</td>
            <td>American Staffordshire TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BORDER COLLIE MIX</td>
            <td>American Staffordshire TerrierBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BOSTON TERRIER MIX</td>
            <td>American Staffordshire TerrierBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BOXER MIX</td>
            <td>American Staffordshire TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BULL TERRIER MIX</td>
            <td>American Staffordshire TerrierBull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BULLDOG MIX</td>
            <td>American Staffordshire TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-BULLMASTIFF MIX</td>
            <td>American Staffordshire TerrierBullmastiff Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-CATAHOULA LEOPARD DOG MIX</td>
            <td>American Staffordshire TerrierCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-CHINESE SHAR-PEI MIX</td>
            <td>American Staffordshire TerrierChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-CHOW CHOW MIX</td>
            <td>American Staffordshire TerrierChow Chow Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-DALMATIAN MIX</td>
            <td>American Staffordshire TerrierDalmatian Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-DOBERMAN PINSCHER MIX</td>
            <td>American Staffordshire TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-DOGO ARGENTINO MIX</td>
            <td>American Staffordshire TerrierDogo Argentino Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-DOGUE DE BORDEAUX MIX</td>
            <td>American Staffordshire TerrierDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GERMAN SHEPHERD DOG MIX</td>
            <td>American Staffordshire TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GERMAN WIREHAIRED POINTER MIX</td>
            <td>American Staffordshire TerrierGerman Wirehaired Pointer Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GOLDEN RETRIEVER MIX</td>
            <td>American Staffordshire TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GORDON SETTER MIX</td>
            <td>American Staffordshire TerrierGordon Setter Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GREAT DANE MIX</td>
            <td>American Staffordshire TerrierGreat Dane Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GREAT PYRENEES MIX</td>
            <td>American Staffordshire TerrierGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-GREYHOUND MIX</td>
            <td>American Staffordshire TerrierGreyhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-LABRADOR RETRIEVER MIX</td>
            <td>American Staffordshire TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-LANCASHIRE HEELER MIX</td>
            <td>American Staffordshire TerrierLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-MASTIFF MIX</td>
            <td>American Staffordshire TerrierMastiff Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-MINIATURE BULL TERRIER MIX</td>
            <td>American Staffordshire TerrierMiniature Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-NEAPOLITAN MASTIFF MIX</td>
            <td>American Staffordshire TerrierNeapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-PORTUGUESE PODENGO MIX</td>
            <td>American Staffordshire TerrierPortuguese Podengo Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-REDBONE COONHOUND MIX</td>
            <td>American Staffordshire TerrierRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-RHODESIAN RIDGEBACK MIX</td>
            <td>American Staffordshire TerrierRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>American Staffordshire TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-TREEING WALKER COONHOUND MIX</td>
            <td>American Staffordshire TerrierTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-WEIMARANER MIX</td>
            <td>American Staffordshire TerrierWeimaraner Mix</td>
        </tr>
        <tr>
            <td>AMERICAN STAFFORDSHIRE TERRIER-WHIPPET MIX</td>
            <td>American Staffordshire TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>AMERICAN WATER SPANIEL</td>
            <td>American Water Spaniel</td>
        </tr>
        <tr>
            <td>AMERICAN WATER SPANIEL-DACHSHUND MIX</td>
            <td>American Water SpanielDachshund Mix</td>
        </tr>
        <tr>
            <td>ANATOLIAN SHEPHERD DOG</td>
            <td>Anatolian Shepherd Dog</td>
        </tr>
        <tr>
            <td>-ANATOLIAN SHEPHERD DOG MIX</td>
            <td>Anatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>ANATOLIAN SHEPHERD DOG-BORDER COLLIE MIX</td>
            <td>Anatolian Shepherd DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>ANATOLIAN SHEPHERD DOG-GREAT PYRENEES MIX</td>
            <td>Anatolian Shepherd DogGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>ANATOLIAN SHEPHERD DOG-LABRADOR RETRIEVER MIX</td>
            <td>Anatolian Shepherd DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>ANATOLIAN SHEPHERD DOG-MASTIFF MIX</td>
            <td>Anatolian Shepherd DogMastiff Mix</td>
        </tr>
        <tr>
            <td>APPENZELLER SENNENHUNDE</td>
            <td>Appenzeller Sennenhunde</td>
        </tr>
        <tr>
            <td>APPENZELLER SENNENHUNDE- MIX</td>
            <td>Appenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>APPENZELLER SENNENHUNDE-BORDER COLLIE MIX</td>
            <td>Appenzeller SennenhundeBorder Collie Mix</td>
        </tr>
        <tr>
            <td>APPENZELLER SENNENHUNDE-COLLIE MIX</td>
            <td>Appenzeller SennenhundeCollie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG</td>
            <td>Australian Cattle Dog</td>
        </tr>
        <tr>
            <td>-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG- MIX</td>
            <td>Australian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Australian Cattle DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Australian Cattle DogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-ANATOLIAN SHEPHERD DOG MIX</td>
            <td>Australian Cattle DogAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-AUSTRALIAN KELPIE MIX</td>
            <td>Australian Cattle DogAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-AUSTRALIAN SHEPHERD MIX</td>
            <td>Australian Cattle DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BASENJI MIX</td>
            <td>Australian Cattle DogBasenji Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BEAGLE MIX</td>
            <td>Australian Cattle DogBeagle Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BEARDED COLLIE MIX</td>
            <td>Australian Cattle DogBearded Collie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BELGIAN SHEEPDOG MIX</td>
            <td>Australian Cattle DogBelgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BERNESE MOUNTAIN DOG MIX</td>
            <td>Australian Cattle DogBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BLUETICK COONHOUND MIX</td>
            <td>Australian Cattle DogBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BORDER COLLIE MIX</td>
            <td>Australian Cattle DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BOXER MIX</td>
            <td>Australian Cattle DogBoxer Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-BULL TERRIER MIX</td>
            <td>Australian Cattle DogBull Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-CARDIGAN WELSH CORGI MIX</td>
            <td>Australian Cattle DogCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-CATAHOULA LEOPARD DOG MIX</td>
            <td>Australian Cattle DogCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-CHOW CHOW MIX</td>
            <td>Australian Cattle DogChow Chow Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-COCKER SPANIEL MIX</td>
            <td>Australian Cattle DogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-CURLY-COATED RETRIEVER MIX</td>
            <td>Australian Cattle DogCurlyCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-DOBERMAN PINSCHER MIX</td>
            <td>Australian Cattle DogDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-GERMAN LONGHAIRED POINTER MIX</td>
            <td>Australian Cattle DogGerman Longhaired Pointer Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-GERMAN SHEPHERD DOG MIX</td>
            <td>Australian Cattle DogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-GREYHOUND MIX</td>
            <td>Australian Cattle DogGreyhound Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-LABRADOR RETRIEVER MIX</td>
            <td>Australian Cattle DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-RAT TERRIER MIX</td>
            <td>Australian Cattle DogRat Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-REDBONE COONHOUND MIX</td>
            <td>Australian Cattle DogRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-ROTTWEILER MIX</td>
            <td>Australian Cattle DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-SHETLAND SHEEPDOG MIX</td>
            <td>Australian Cattle DogShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-SIBERIAN HUSKY MIX</td>
            <td>Australian Cattle DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Australian Cattle DogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-TREEING WALKER COONHOUND MIX</td>
            <td>Australian Cattle DogTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN CATTLE DOG-WEIMARANER MIX</td>
            <td>Australian Cattle DogWeimaraner Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE</td>
            <td>Australian Kelpie</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Australian KelpieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-BASENJI MIX</td>
            <td>Australian KelpieBasenji Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-BORDER COLLIE MIX</td>
            <td>Australian KelpieBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-LABRADOR RETRIEVER MIX</td>
            <td>Australian KelpieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-MINIATURE SCHNAUZER MIX</td>
            <td>Australian KelpieMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-ROTTWEILER MIX</td>
            <td>Australian KelpieRottweiler Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN KELPIE-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Australian KelpieStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN LABRADOODLE</td>
            <td>Australian Labradoodle</td>
        </tr>
        <tr>
            <td>AUSTRALIAN LABRADOODLE-POODLE MIX</td>
            <td>Australian LabradoodlePoodle Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD</td>
            <td>Australian Shepherd</td>
        </tr>
        <tr>
            <td>-AUSTRALIAN SHEPHERD MIX</td>
            <td>Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD- MIX</td>
            <td>Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-ALASKAN MALAMUTE MIX</td>
            <td>Australian ShepherdAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Australian ShepherdAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Australian ShepherdAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-BASENJI MIX</td>
            <td>Australian ShepherdBasenji Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-BEAGLE MIX</td>
            <td>Australian ShepherdBeagle Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-BEARDED COLLIE MIX</td>
            <td>Australian ShepherdBearded Collie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-BLOODHOUND MIX</td>
            <td>Australian ShepherdBloodhound Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-BORDER COLLIE MIX</td>
            <td>Australian ShepherdBorder Collie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-CARDIGAN WELSH CORGI MIX</td>
            <td>Australian ShepherdCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-CATAHOULA LEOPARD DOG MIX</td>
            <td>Australian ShepherdCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-CHOW CHOW MIX</td>
            <td>Australian ShepherdChow Chow Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-COCKER SPANIEL MIX</td>
            <td>Australian ShepherdCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-COLLIE MIX</td>
            <td>Australian ShepherdCollie Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-DOBERMAN PINSCHER MIX</td>
            <td>Australian ShepherdDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-ENGLISH COCKER SPANIEL MIX</td>
            <td>Australian ShepherdEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-FLAT-COATED RETRIEVER MIX</td>
            <td>Australian ShepherdFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-GERMAN SHEPHERD DOG MIX</td>
            <td>Australian ShepherdGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-GOLDEN RETRIEVER MIX</td>
            <td>Australian ShepherdGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-GREAT PYRENEES MIX</td>
            <td>Australian ShepherdGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-LABRADOR RETRIEVER MIX</td>
            <td>Australian ShepherdLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-PEMBROKE WELSH CORGI MIX</td>
            <td>Australian ShepherdPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-POODLE MIX</td>
            <td>Australian ShepherdPoodle Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-PUG MIX</td>
            <td>Australian ShepherdPug Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-RHODESIAN RIDGEBACK MIX</td>
            <td>Australian ShepherdRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-ROTTWEILER MIX</td>
            <td>Australian ShepherdRottweiler Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-SCHIPPERKE MIX</td>
            <td>Australian ShepherdSchipperke Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-SHETLAND SHEEPDOG MIX</td>
            <td>Australian ShepherdShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-SHIBA INU MIX</td>
            <td>Australian ShepherdShiba Inu Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-SHIH TZU MIX</td>
            <td>Australian ShepherdShih Tzu Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-SIBERIAN HUSKY MIX</td>
            <td>Australian ShepherdSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-ST. BERNARD MIX</td>
            <td>Australian ShepherdSt. Bernard Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-STANDARD POODLE MIX</td>
            <td>Australian ShepherdStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN SHEPHERD-WEIMARANER MIX</td>
            <td>Australian ShepherdWeimaraner Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN TERRIER</td>
            <td>Australian Terrier</td>
        </tr>
        <tr>
            <td>AUSTRALIAN TERRIER-LOWCHEN MIX</td>
            <td>Australian TerrierLowchen Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN TERRIER-PARSON RUSSELL TERRIER MIX</td>
            <td>Australian TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN TERRIER-ROTTWEILER MIX</td>
            <td>Australian TerrierRottweiler Mix</td>
        </tr>
        <tr>
            <td>AUSTRALIAN TERRIER-YORKSHIRE TERRIER MIX</td>
            <td>Australian TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BARBET</td>
            <td>Barbet</td>
        </tr>
        <tr>
            <td>BASENJI</td>
            <td>Basenji</td>
        </tr>
        <tr>
            <td>BASENJI- MIX</td>
            <td>Basenji Mix</td>
        </tr>
        <tr>
            <td>BASENJI-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>BasenjiAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BASENJI-AMERICAN WATER SPANIEL MIX</td>
            <td>BasenjiAmerican Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>BASENJI-AUSTRALIAN CATTLE DOG MIX</td>
            <td>BasenjiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>BASENJI-BEAGLE MIX</td>
            <td>BasenjiBeagle Mix</td>
        </tr>
        <tr>
            <td>BASENJI-CARDIGAN WELSH CORGI MIX</td>
            <td>BasenjiCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>BASENJI-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>BasenjiEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BASENJI-GERMAN SHEPHERD DOG MIX</td>
            <td>BasenjiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BASENJI-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>BasenjiGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>BASENJI-MANCHESTER TERRIER MIX</td>
            <td>BasenjiManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>BASENJI-RUSSELL TERRIER MIX</td>
            <td>BasenjiRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BASENJI-SHIBA INU MIX</td>
            <td>BasenjiShiba Inu Mix</td>
        </tr>
        <tr>
            <td>BASENJI-SIBERIAN HUSKY MIX</td>
            <td>BasenjiSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BASENJI-WHIPPET MIX</td>
            <td>BasenjiWhippet Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND</td>
            <td>Basset Hound</td>
        </tr>
        <tr>
            <td>BASSET HOUND- MIX</td>
            <td>Basset Hound Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AIREDALE TERRIER MIX</td>
            <td>Basset HoundAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AMERICAN ENGLISH COONHOUND MIX</td>
            <td>Basset HoundAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Basset HoundAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Basset HoundAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Basset HoundAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-AUSTRALIAN SHEPHERD MIX</td>
            <td>Basset HoundAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-BEAGLE MIX</td>
            <td>Basset HoundBeagle Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-BOSTON TERRIER MIX</td>
            <td>Basset HoundBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-CARDIGAN WELSH CORGI MIX</td>
            <td>Basset HoundCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-COCKER SPANIEL MIX</td>
            <td>Basset HoundCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-DACHSHUND MIX</td>
            <td>Basset HoundDachshund Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-GERMAN SHEPHERD DOG MIX</td>
            <td>Basset HoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-GREAT PYRENEES MIX</td>
            <td>Basset HoundGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-LABRADOR RETRIEVER MIX</td>
            <td>Basset HoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-PEMBROKE WELSH CORGI MIX</td>
            <td>Basset HoundPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-POINTER MIX</td>
            <td>Basset HoundPointer Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-POODLE MIX</td>
            <td>Basset HoundPoodle Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-ROTTWEILER MIX</td>
            <td>Basset HoundRottweiler Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-RUSSELL TERRIER MIX</td>
            <td>Basset HoundRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BASSET HOUND-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Basset HoundStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE</td>
            <td>Beagle</td>
        </tr>
        <tr>
            <td>-BEAGLE MIX</td>
            <td>Beagle Mix</td>
        </tr>
        <tr>
            <td>BEAGLE- MIX</td>
            <td>Beagle Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-AMERICAN ENGLISH COONHOUND MIX</td>
            <td>BeagleAmerican English Coonhound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-AMERICAN ESKIMO DOG MIX</td>
            <td>BeagleAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-AMERICAN FOXHOUND MIX</td>
            <td>BeagleAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-AUSTRALIAN CATTLE DOG MIX</td>
            <td>BeagleAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BASSET HOUND MIX</td>
            <td>BeagleBasset Hound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BLUETICK COONHOUND MIX</td>
            <td>BeagleBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BORDER COLLIE MIX</td>
            <td>BeagleBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BORDER TERRIER MIX</td>
            <td>BeagleBorder Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BOSTON TERRIER MIX</td>
            <td>BeagleBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BOXER MIX</td>
            <td>BeagleBoxer Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-BULLDOG MIX</td>
            <td>BeagleBulldog Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-CAVALIER KING CHARLES SPANIEL MIX</td>
            <td>BeagleCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-CHIHUAHUA MIX</td>
            <td>BeagleChihuahua Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-CHINESE SHAR-PEI MIX</td>
            <td>BeagleChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-CHOW CHOW MIX</td>
            <td>BeagleChow Chow Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-COCKER SPANIEL MIX</td>
            <td>BeagleCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-COLLIE MIX</td>
            <td>BeagleCollie Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-DACHSHUND MIX</td>
            <td>BeagleDachshund Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-GERMAN SHEPHERD DOG MIX</td>
            <td>BeagleGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-GOLDEN RETRIEVER MIX</td>
            <td>BeagleGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-GREYHOUND MIX</td>
            <td>BeagleGreyhound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-JACK RUSSELL TERRIER MIX</td>
            <td>BeagleJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-LABRADOR RETRIEVER MIX</td>
            <td>BeagleLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-MINIATURE SCHNAUZER MIX</td>
            <td>BeagleMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-PARSON RUSSELL TERRIER MIX</td>
            <td>BeagleParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-PEKINGESE MIX</td>
            <td>BeaglePekingese Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-POINTER MIX</td>
            <td>BeaglePointer Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-POODLE MIX</td>
            <td>BeaglePoodle Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-PUG MIX</td>
            <td>BeaglePug Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-RAT TERRIER MIX</td>
            <td>BeagleRat Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-RUSSELL TERRIER MIX</td>
            <td>BeagleRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-SCHIPPERKE MIX</td>
            <td>BeagleSchipperke Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-SHETLAND SHEEPDOG MIX</td>
            <td>BeagleShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-SIBERIAN HUSKY MIX</td>
            <td>BeagleSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-SMOOTH FOX TERRIER MIX</td>
            <td>BeagleSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-TOY FOX TERRIER MIX</td>
            <td>BeagleToy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-TREEING WALKER COONHOUND MIX</td>
            <td>BeagleTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>BEAGLE-WHIPPET MIX</td>
            <td>BeagleWhippet Mix</td>
        </tr>
        <tr>
            <td>BEAGLIER</td>
            <td>Beaglier</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE</td>
            <td>Bearded Collie</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-BEAGLE MIX</td>
            <td>Bearded CollieBeagle Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-BERNESE MOUNTAIN DOG MIX</td>
            <td>Bearded CollieBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-BORDER COLLIE MIX</td>
            <td>Bearded CollieBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-LABRADOR RETRIEVER MIX</td>
            <td>Bearded CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-SHIH TZU MIX</td>
            <td>Bearded CollieShih Tzu Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-SOFT COATED WHEATEN TERRIER MIX</td>
            <td>Bearded CollieSoft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>BEARDED COLLIE-TIBETAN TERRIER MIX</td>
            <td>Bearded CollieTibetan Terrier Mix</td>
        </tr>
        <tr>
            <td>BEAUCERON</td>
            <td>Beauceron</td>
        </tr>
        <tr>
            <td>BEAUCERON-ROTTWEILER MIX</td>
            <td>BeauceronRottweiler Mix</td>
        </tr>
        <tr>
            <td>BEDLINGTON TERRIER</td>
            <td>Bedlington Terrier</td>
        </tr>
        <tr>
            <td>BEDLINGTON TERRIER-BELGIAN LAEKENOIS MIX</td>
            <td>Bedlington TerrierBelgian Laekenois Mix</td>
        </tr>
        <tr>
            <td>BEDLINGTON TERRIER-WHIPPET MIX</td>
            <td>Bedlington TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>BELGIAN LAEKENOIS</td>
            <td>Belgian Laekenois</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS</td>
            <td>Belgian Malinois</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS- MIX</td>
            <td>Belgian Malinois Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Belgian MalinoisAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-BELGIAN TERVUREN MIX</td>
            <td>Belgian MalinoisBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-BORDER COLLIE MIX</td>
            <td>Belgian MalinoisBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-CHINESE SHAR-PEI MIX</td>
            <td>Belgian MalinoisChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-CHOW CHOW MIX</td>
            <td>Belgian MalinoisChow Chow Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-DUTCH SHEPHERD MIX</td>
            <td>Belgian MalinoisDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-GERMAN SHEPHERD DOG MIX</td>
            <td>Belgian MalinoisGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-LABRADOR RETRIEVER MIX</td>
            <td>Belgian MalinoisLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BELGIAN MALINOIS-SIBERIAN HUSKY MIX</td>
            <td>Belgian MalinoisSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG</td>
            <td>Belgian Sheepdog</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG- MIX</td>
            <td>Belgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-BORDER COLLIE MIX</td>
            <td>Belgian SheepdogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-CHOW CHOW MIX</td>
            <td>Belgian SheepdogChow Chow Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-DUTCH SHEPHERD MIX</td>
            <td>Belgian SheepdogDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-GERMAN SHEPHERD DOG MIX</td>
            <td>Belgian SheepdogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-GOLDEN RETRIEVER MIX</td>
            <td>Belgian SheepdogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BELGIAN SHEEPDOG-LHASA APSO MIX</td>
            <td>Belgian SheepdogLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>BELGIAN TERVUREN</td>
            <td>Belgian Tervuren</td>
        </tr>
        <tr>
            <td>BELGIAN TERVUREN-BASENJI MIX</td>
            <td>Belgian TervurenBasenji Mix</td>
        </tr>
        <tr>
            <td>BELGIAN TERVUREN-BORDER COLLIE MIX</td>
            <td>Belgian TervurenBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BELGIAN TERVUREN-BOSTON TERRIER MIX</td>
            <td>Belgian TervurenBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>BELGIAN TERVUREN-WHIPPET MIX</td>
            <td>Belgian TervurenWhippet Mix</td>
        </tr>
        <tr>
            <td>BERGAMASCO-OLD ENGLISH SHEEPDOG MIX</td>
            <td>BergamascoOld English Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BERGER PICARD</td>
            <td>Berger Picard</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG</td>
            <td>Bernese Mountain Dog</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-BORDER COLLIE MIX</td>
            <td>Bernese Mountain DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-CHOW CHOW MIX</td>
            <td>Bernese Mountain DogChow Chow Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>Bernese Mountain DogEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-GOLDEN RETRIEVER MIX</td>
            <td>Bernese Mountain DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-GREAT PYRENEES MIX</td>
            <td>Bernese Mountain DogGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-GREATER SWISS MOUNTAIN DOG MIX</td>
            <td>Bernese Mountain DogGreater Swiss Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-LABRADOR RETRIEVER MIX</td>
            <td>Bernese Mountain DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-POODLE MIX</td>
            <td>Bernese Mountain DogPoodle Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-ROTTWEILER MIX</td>
            <td>Bernese Mountain DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>BERNESE MOUNTAIN DOG-STANDARD POODLE MIX</td>
            <td>Bernese Mountain DogStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE</td>
            <td>Bichon Frise</td>
        </tr>
        <tr>
            <td>-BICHON FRISE MIX</td>
            <td>Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE- MIX</td>
            <td>Bichon Frise Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-AMERICAN ESKIMO DOG MIX</td>
            <td>Bichon FriseAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-CAVALIER KING CHARLES SPANIEL MIX</td>
            <td>Bichon FriseCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-CHINESE CRESTED MIX</td>
            <td>Bichon FriseChinese Crested Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-COCKER SPANIEL MIX</td>
            <td>Bichon FriseCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-GOLDEN RETRIEVER MIX</td>
            <td>Bichon FriseGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-HAVANESE MIX</td>
            <td>Bichon FriseHavanese Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-JACK RUSSELL TERRIER MIX</td>
            <td>Bichon FriseJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-LHASA APSO MIX</td>
            <td>Bichon FriseLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-MALTESE MIX</td>
            <td>Bichon FriseMaltese Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-MINIATURE SCHNAUZER MIX</td>
            <td>Bichon FriseMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-POMERANIAN MIX</td>
            <td>Bichon FrisePomeranian Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-POODLE MIX</td>
            <td>Bichon FrisePoodle Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-SHIH TZU MIX</td>
            <td>Bichon FriseShih Tzu Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-WEST HIGHLAND WHITE TERRIER MIX</td>
            <td>Bichon FriseWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>BICHON FRISE-YORKSHIRE TERRIER MIX</td>
            <td>Bichon FriseYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND</td>
            <td>Black and Tan Coonhound</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND- MIX</td>
            <td>Black and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND-BEAGLE MIX</td>
            <td>Black and Tan CoonhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND-GERMAN SHEPHERD DOG MIX</td>
            <td>Black and Tan CoonhoundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND-GOLDEN RETRIEVER MIX</td>
            <td>Black and Tan CoonhoundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND-LABRADOR RETRIEVER MIX</td>
            <td>Black and Tan CoonhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BLACK AND TAN COONHOUND-PLOTT MIX</td>
            <td>Black and Tan CoonhoundPlott Mix</td>
        </tr>
        <tr>
            <td>BLACK RUSSIAN TERRIER</td>
            <td>Black Russian Terrier</td>
        </tr>
        <tr>
            <td>BLOODHOUND</td>
            <td>Bloodhound</td>
        </tr>
        <tr>
            <td>BLOODHOUND-BEAGLE MIX</td>
            <td>BloodhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>BLOODHOUND-BLACK AND TAN COONHOUND MIX</td>
            <td>BloodhoundBlack and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>BLOODHOUND-BULL TERRIER MIX</td>
            <td>BloodhoundBull Terrier Mix</td>
        </tr>
        <tr>
            <td>BLOODHOUND-IRISH SETTER MIX</td>
            <td>BloodhoundIrish Setter Mix</td>
        </tr>
        <tr>
            <td>BLOODHOUND-LABRADOR RETRIEVER MIX</td>
            <td>BloodhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND</td>
            <td>Bluetick Coonhound</td>
        </tr>
        <tr>
            <td>-BLUETICK COONHOUND MIX</td>
            <td>Bluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-BEAGLE MIX</td>
            <td>Bluetick CoonhoundBeagle Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>Bluetick CoonhoundGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-JACK RUSSELL TERRIER MIX</td>
            <td>Bluetick CoonhoundJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-POINTER MIX</td>
            <td>Bluetick CoonhoundPointer Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-ROTTWEILER MIX</td>
            <td>Bluetick CoonhoundRottweiler Mix</td>
        </tr>
        <tr>
            <td>BLUETICK COONHOUND-TREEING WALKER COONHOUND MIX</td>
            <td>Bluetick CoonhoundTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>BOERBOEL</td>
            <td>Boerboel</td>
        </tr>
        <tr>
            <td>BOLOGNESE</td>
            <td>Bolognese</td>
        </tr>
        <tr>
            <td>BORDER COLLIE</td>
            <td>Border Collie</td>
        </tr>
        <tr>
            <td>-BORDER COLLIE MIX</td>
            <td>Border Collie Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE- MIX</td>
            <td>Border Collie Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AFFENPINSCHER MIX</td>
            <td>Border CollieAffenpinscher Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AKITA MIX</td>
            <td>Border CollieAkita Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AMERICAN ESKIMO DOG MIX</td>
            <td>Border CollieAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AMERICAN FOXHOUND MIX</td>
            <td>Border CollieAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Border CollieAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Border CollieAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Border CollieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AUSTRALIAN KELPIE MIX</td>
            <td>Border CollieAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-AUSTRALIAN SHEPHERD MIX</td>
            <td>Border CollieAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BEAGLE MIX</td>
            <td>Border CollieBeagle Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BEARDED COLLIE MIX</td>
            <td>Border CollieBearded Collie Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BEAUCERON MIX</td>
            <td>Border CollieBeauceron Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BELGIAN SHEEPDOG MIX</td>
            <td>Border CollieBelgian Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BELGIAN TERVUREN MIX</td>
            <td>Border CollieBelgian Tervuren Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BERNESE MOUNTAIN DOG MIX</td>
            <td>Border CollieBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BLOODHOUND MIX</td>
            <td>Border CollieBloodhound Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BLUETICK COONHOUND MIX</td>
            <td>Border CollieBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BORZOI MIX</td>
            <td>Border CollieBorzoi Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BOXER MIX</td>
            <td>Border CollieBoxer Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BRITTANY MIX</td>
            <td>Border CollieBrittany Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-BULL TERRIER MIX</td>
            <td>Border CollieBull Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-CAVALIER KING CHARLES SPANIEL MIX</td>
            <td>Border CollieCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-CHOW CHOW MIX</td>
            <td>Border CollieChow Chow Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-COCKER SPANIEL MIX</td>
            <td>Border CollieCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-COLLIE MIX</td>
            <td>Border CollieCollie Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-DALMATIAN MIX</td>
            <td>Border CollieDalmatian Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-ENGLISH COCKER SPANIEL MIX</td>
            <td>Border CollieEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-ENGLISH SETTER MIX</td>
            <td>Border CollieEnglish Setter Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>Border CollieEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-FIELD SPANIEL MIX</td>
            <td>Border CollieField Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-FLAT-COATED RETRIEVER MIX</td>
            <td>Border CollieFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GERMAN SHEPHERD DOG MIX</td>
            <td>Border CollieGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>Border CollieGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GOLDEN RETRIEVER MIX</td>
            <td>Border CollieGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GREAT DANE MIX</td>
            <td>Border CollieGreat Dane Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GREAT PYRENEES MIX</td>
            <td>Border CollieGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-GREYHOUND MIX</td>
            <td>Border CollieGreyhound Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-ICELANDIC SHEEPDOG MIX</td>
            <td>Border CollieIcelandic Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-IRISH SETTER MIX</td>
            <td>Border CollieIrish Setter Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-IRISH WATER SPANIEL MIX</td>
            <td>Border CollieIrish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-JACK RUSSELL TERRIER MIX</td>
            <td>Border CollieJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-KEESHOND MIX</td>
            <td>Border CollieKeeshond Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-KOOIKERHONDJE MIX</td>
            <td>Border CollieKooikerhondje Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-LABRADOR RETRIEVER MIX</td>
            <td>Border CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-LANCASHIRE HEELER MIX</td>
            <td>Border CollieLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-MINIATURE AUSTRALIAN SHEPHERD MIX</td>
            <td>Border CollieMiniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-MINIATURE PINSCHER MIX</td>
            <td>Border CollieMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-NEWFOUNDLAND MIX</td>
            <td>Border CollieNewfoundland Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-PARSON RUSSELL TERRIER MIX</td>
            <td>Border CollieParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-PEMBROKE WELSH CORGI MIX</td>
            <td>Border ColliePembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-POINTER MIX</td>
            <td>Border ColliePointer Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-POMERANIAN MIX</td>
            <td>Border ColliePomeranian Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-POODLE MIX</td>
            <td>Border ColliePoodle Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-RHODESIAN RIDGEBACK MIX</td>
            <td>Border CollieRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-ROTTWEILER MIX</td>
            <td>Border CollieRottweiler Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-SALUKI MIX</td>
            <td>Border CollieSaluki Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-SHETLAND SHEEPDOG MIX</td>
            <td>Border CollieShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-SIBERIAN HUSKY MIX</td>
            <td>Border CollieSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-SOFT COATED WHEATEN TERRIER MIX</td>
            <td>Border CollieSoft Coated Wheaten Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Border CollieStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-STANDARD POODLE MIX</td>
            <td>Border CollieStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-STANDARD SCHNAUZER MIX</td>
            <td>Border CollieStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-WELSH SPRINGER SPANIEL MIX</td>
            <td>Border CollieWelsh Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-WEST HIGHLAND WHITE TERRIER MIX</td>
            <td>Border CollieWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-WHIPPET MIX</td>
            <td>Border CollieWhippet Mix</td>
        </tr>
        <tr>
            <td>BORDER COLLIE-WIRE FOX TERRIER MIX</td>
            <td>Border CollieWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER</td>
            <td>Border Terrier</td>
        </tr>
        <tr>
            <td>BORDER TERRIER- MIX</td>
            <td>Border Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-BEAGLE MIX</td>
            <td>Border TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-BERNESE MOUNTAIN DOG MIX</td>
            <td>Border TerrierBernese Mountain Dog Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-CAIRN TERRIER MIX</td>
            <td>Border TerrierCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-DACHSHUND MIX</td>
            <td>Border TerrierDachshund Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-ENGLISH COCKER SPANIEL MIX</td>
            <td>Border TerrierEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-GOLDEN RETRIEVER MIX</td>
            <td>Border TerrierGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-LAKELAND TERRIER MIX</td>
            <td>Border TerrierLakeland Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-PARSON RUSSELL TERRIER MIX</td>
            <td>Border TerrierParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-POODLE MIX</td>
            <td>Border TerrierPoodle Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-PUG MIX</td>
            <td>Border TerrierPug Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-RUSSELL TERRIER MIX</td>
            <td>Border TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-SHIH TZU MIX</td>
            <td>Border TerrierShih Tzu Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Border TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-STANDARD SCHNAUZER MIX</td>
            <td>Border TerrierStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>BORDER TERRIER-WEST HIGHLAND WHITE TERRIER MIX</td>
            <td>Border TerrierWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>BORZOI</td>
            <td>Borzoi</td>
        </tr>
        <tr>
            <td>BORZOI-WHIPPET MIX</td>
            <td>BorzoiWhippet Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER</td>
            <td>Boston Terrier</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Boston TerrierAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Boston TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-BEAGLE MIX</td>
            <td>Boston TerrierBeagle Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-BULLDOG MIX</td>
            <td>Boston TerrierBulldog Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-CHIHUAHUA MIX</td>
            <td>Boston TerrierChihuahua Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-DACHSHUND MIX</td>
            <td>Boston TerrierDachshund Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-DANISH-SWEDISH FARMDOG MIX</td>
            <td>Boston TerrierDanishSwedish Farmdog Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-DOBERMAN PINSCHER MIX</td>
            <td>Boston TerrierDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-FRENCH BULLDOG MIX</td>
            <td>Boston TerrierFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-LABRADOR RETRIEVER MIX</td>
            <td>Boston TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-POMERANIAN MIX</td>
            <td>Boston TerrierPomeranian Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-PUG MIX</td>
            <td>Boston TerrierPug Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-RAT TERRIER MIX</td>
            <td>Boston TerrierRat Terrier Mix</td>
        </tr>
        <tr>
            <td>BOSTON TERRIER-RUSSELL TERRIER MIX</td>
            <td>Boston TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BOUVIER DES FLANDRES</td>
            <td>Bouvier des Flandres</td>
        </tr>
        <tr>
            <td>BOUVIER DES FLANDRES-AIREDALE TERRIER MIX</td>
            <td>Bouvier des FlandresAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>BOUVIER DES FLANDRES-STANDARD POODLE MIX</td>
            <td>Bouvier des FlandresStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>BOXER</td>
            <td>Boxer</td>
        </tr>
        <tr>
            <td>-BOXER MIX</td>
            <td>Boxer Mix</td>
        </tr>
        <tr>
            <td>BOXER- MIX</td>
            <td>Boxer Mix</td>
        </tr>
        <tr>
            <td>BOXER-AKITA MIX</td>
            <td>BoxerAkita Mix</td>
        </tr>
        <tr>
            <td>BOXER-AMERICAN FOXHOUND MIX</td>
            <td>BoxerAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-AMERICAN PIT BULL TERRIER MIX</td>
            <td>BoxerAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>BoxerAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-AUSTRALIAN CATTLE DOG MIX</td>
            <td>BoxerAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>BOXER-AUSTRALIAN SHEPHERD MIX</td>
            <td>BoxerAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>BOXER-BLOODHOUND MIX</td>
            <td>BoxerBloodhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-BORDER COLLIE MIX</td>
            <td>BoxerBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BOXER-BOSTON TERRIER MIX</td>
            <td>BoxerBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-BULL TERRIER MIX</td>
            <td>BoxerBull Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-BULLDOG MIX</td>
            <td>BoxerBulldog Mix</td>
        </tr>
        <tr>
            <td>BOXER-BULLMASTIFF MIX</td>
            <td>BoxerBullmastiff Mix</td>
        </tr>
        <tr>
            <td>BOXER-COCKER SPANIEL MIX</td>
            <td>BoxerCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BOXER-DACHSHUND MIX</td>
            <td>BoxerDachshund Mix</td>
        </tr>
        <tr>
            <td>BOXER-DALMATIAN MIX</td>
            <td>BoxerDalmatian Mix</td>
        </tr>
        <tr>
            <td>BOXER-DOBERMAN PINSCHER MIX</td>
            <td>BoxerDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>BOXER-DUTCH SHEPHERD MIX</td>
            <td>BoxerDutch Shepherd Mix</td>
        </tr>
        <tr>
            <td>BOXER-ENGLISH FOXHOUND MIX</td>
            <td>BoxerEnglish Foxhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>BoxerEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BOXER-GERMAN SHEPHERD DOG MIX</td>
            <td>BoxerGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BOXER-GOLDEN RETRIEVER MIX</td>
            <td>BoxerGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BOXER-GREAT DANE MIX</td>
            <td>BoxerGreat Dane Mix</td>
        </tr>
        <tr>
            <td>BOXER-GREAT PYRENEES MIX</td>
            <td>BoxerGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>BOXER-GREYHOUND MIX</td>
            <td>BoxerGreyhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-IBIZAN HOUND MIX</td>
            <td>BoxerIbizan Hound Mix</td>
        </tr>
        <tr>
            <td>BOXER-JINDO MIX</td>
            <td>BoxerJindo Mix</td>
        </tr>
        <tr>
            <td>BOXER-LABRADOR RETRIEVER MIX</td>
            <td>BoxerLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BOXER-MANCHESTER TERRIER MIX</td>
            <td>BoxerManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-MASTIFF MIX</td>
            <td>BoxerMastiff Mix</td>
        </tr>
        <tr>
            <td>BOXER-POODLE MIX</td>
            <td>BoxerPoodle Mix</td>
        </tr>
        <tr>
            <td>BOXER-PUG MIX</td>
            <td>BoxerPug Mix</td>
        </tr>
        <tr>
            <td>BOXER-REDBONE COONHOUND MIX</td>
            <td>BoxerRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-RHODESIAN RIDGEBACK MIX</td>
            <td>BoxerRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>BOXER-ROTTWEILER MIX</td>
            <td>BoxerRottweiler Mix</td>
        </tr>
        <tr>
            <td>BOXER-RUSSELL TERRIER MIX</td>
            <td>BoxerRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-SIBERIAN HUSKY MIX</td>
            <td>BoxerSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BOXER-ST. BERNARD MIX</td>
            <td>BoxerSt. Bernard Mix</td>
        </tr>
        <tr>
            <td>BOXER-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>BoxerStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BOXER-TREEING WALKER COONHOUND MIX</td>
            <td>BoxerTreeing Walker Coonhound Mix</td>
        </tr>
        <tr>
            <td>BOXER-VIZSLA MIX</td>
            <td>BoxerVizsla Mix</td>
        </tr>
        <tr>
            <td>BOXER-WEIMARANER MIX</td>
            <td>BoxerWeimaraner Mix</td>
        </tr>
        <tr>
            <td>BOYKIN SPANIEL</td>
            <td>Boykin Spaniel</td>
        </tr>
        <tr>
            <td>BOYKIN SPANIEL- MIX</td>
            <td>Boykin Spaniel Mix</td>
        </tr>
        <tr>
            <td>BOYKIN SPANIEL-DEUTSCHER WACHTELHUND MIX</td>
            <td>Boykin SpanielDeutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>BOYKIN SPANIEL-ENGLISH COCKER SPANIEL MIX</td>
            <td>Boykin SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BOYKIN SPANIEL-IRISH SETTER MIX</td>
            <td>Boykin SpanielIrish Setter Mix</td>
        </tr>
        <tr>
            <td>BRAQUE DU BOURBONNAIS</td>
            <td>Braque du Bourbonnais</td>
        </tr>
        <tr>
            <td>BRIARD</td>
            <td>Briard</td>
        </tr>
        <tr>
            <td>BRITTANY</td>
            <td>Brittany</td>
        </tr>
        <tr>
            <td>BRITTANY-BASSET HOUND MIX</td>
            <td>BrittanyBasset Hound Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-BORDER COLLIE MIX</td>
            <td>BrittanyBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>BrittanyEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-GERMAN SHEPHERD DOG MIX</td>
            <td>BrittanyGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>BrittanyGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-GOLDEN RETRIEVER MIX</td>
            <td>BrittanyGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-IRISH SETTER MIX</td>
            <td>BrittanyIrish Setter Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-LABRADOR RETRIEVER MIX</td>
            <td>BrittanyLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-PEKINGESE MIX</td>
            <td>BrittanyPekingese Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-POINTER MIX</td>
            <td>BrittanyPointer Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-POODLE MIX</td>
            <td>BrittanyPoodle Mix</td>
        </tr>
        <tr>
            <td>BRITTANY-SIBERIAN HUSKY MIX</td>
            <td>BrittanySiberian Husky Mix</td>
        </tr>
        <tr>
            <td>BRUSSELS GRIFFON</td>
            <td>Brussels Griffon</td>
        </tr>
        <tr>
            <td>BRUSSELS GRIFFON-BORDER TERRIER MIX</td>
            <td>Brussels GriffonBorder Terrier Mix</td>
        </tr>
        <tr>
            <td>BRUSSELS GRIFFON-POODLE MIX</td>
            <td>Brussels GriffonPoodle Mix</td>
        </tr>
        <tr>
            <td>BRUSSELS GRIFFON-PUG MIX</td>
            <td>Brussels GriffonPug Mix</td>
        </tr>
        <tr>
            <td>BRUSSELS GRIFFON-SHIH TZU MIX</td>
            <td>Brussels GriffonShih Tzu Mix</td>
        </tr>
        <tr>
            <td>BUGG</td>
            <td>Bugg</td>
        </tr>
        <tr>
            <td>BULL TERRIER</td>
            <td>Bull Terrier</td>
        </tr>
        <tr>
            <td>BULL TERRIER-AMERICAN FOXHOUND MIX</td>
            <td>Bull TerrierAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>BULL TERRIER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Bull TerrierAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BULL TERRIER-BOXER MIX</td>
            <td>Bull TerrierBoxer Mix</td>
        </tr>
        <tr>
            <td>BULL TERRIER-LABRADOR RETRIEVER MIX</td>
            <td>Bull TerrierLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BULL TERRIER-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Bull TerrierStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BULL TERRIER-WHIPPET MIX</td>
            <td>Bull TerrierWhippet Mix</td>
        </tr>
        <tr>
            <td>BULLBOXER</td>
            <td>BullBoxer</td>
        </tr>
        <tr>
            <td>BULLDOG</td>
            <td>Bulldog</td>
        </tr>
        <tr>
            <td>BULLDOG-AMERICAN PIT BULL TERRIER MIX</td>
            <td>BulldogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>BulldogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-BASSET HOUND MIX</td>
            <td>BulldogBasset Hound Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-BEAGLE MIX</td>
            <td>BulldogBeagle Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-BOSTON TERRIER MIX</td>
            <td>BulldogBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-BOXER MIX</td>
            <td>BulldogBoxer Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-BULLMASTIFF MIX</td>
            <td>BulldogBullmastiff Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-CHESAPEAKE BAY RETRIEVER MIX</td>
            <td>BulldogChesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-COCKER SPANIEL MIX</td>
            <td>BulldogCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-DOGO ARGENTINO MIX</td>
            <td>BulldogDogo Argentino Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-FRENCH BULLDOG MIX</td>
            <td>BulldogFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-GERMAN SHEPHERD DOG MIX</td>
            <td>BulldogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>BulldogGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-GREAT DANE MIX</td>
            <td>BulldogGreat Dane Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-LABRADOR RETRIEVER MIX</td>
            <td>BulldogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-MASTIFF MIX</td>
            <td>BulldogMastiff Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-NEAPOLITAN MASTIFF MIX</td>
            <td>BulldogNeapolitan Mastiff Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-PUG MIX</td>
            <td>BulldogPug Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-RHODESIAN RIDGEBACK MIX</td>
            <td>BulldogRhodesian Ridgeback Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-ROTTWEILER MIX</td>
            <td>BulldogRottweiler Mix</td>
        </tr>
        <tr>
            <td>BULLDOG-WIREHAIRED POINTING GRIFFON MIX</td>
            <td>BulldogWirehaired Pointing Griffon Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF</td>
            <td>Bullmastiff</td>
        </tr>
        <tr>
            <td>BULLMASTIFF- MIX</td>
            <td>Bullmastiff Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-AMERICAN PIT BULL TERRIER MIX</td>
            <td>BullmastiffAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>BullmastiffAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-BORDER COLLIE MIX</td>
            <td>BullmastiffBorder Collie Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-BOXER MIX</td>
            <td>BullmastiffBoxer Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-BULL TERRIER MIX</td>
            <td>BullmastiffBull Terrier Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-BULLDOG MIX</td>
            <td>BullmastiffBulldog Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-CHINESE SHAR-PEI MIX</td>
            <td>BullmastiffChinese SharPei Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-DOGUE DE BORDEAUX MIX</td>
            <td>BullmastiffDogue de Bordeaux Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-GERMAN SHEPHERD DOG MIX</td>
            <td>BullmastiffGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-LABRADOR RETRIEVER MIX</td>
            <td>BullmastiffLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-REDBONE COONHOUND MIX</td>
            <td>BullmastiffRedbone Coonhound Mix</td>
        </tr>
        <tr>
            <td>BULLMASTIFF-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>BullmastiffStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER</td>
            <td>Cairn Terrier</td>
        </tr>
        <tr>
            <td>-CAIRN TERRIER MIX</td>
            <td>Cairn Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-AIREDALE TERRIER MIX</td>
            <td>Cairn TerrierAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-AUSTRALIAN TERRIER MIX</td>
            <td>Cairn TerrierAustralian Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-COCKER SPANIEL MIX</td>
            <td>Cairn TerrierCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-GERMAN SHEPHERD DOG MIX</td>
            <td>Cairn TerrierGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-JACK RUSSELL TERRIER MIX</td>
            <td>Cairn TerrierJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-LHASA APSO MIX</td>
            <td>Cairn TerrierLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-POMERANIAN MIX</td>
            <td>Cairn TerrierPomeranian Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-POODLE MIX</td>
            <td>Cairn TerrierPoodle Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-RUSSELL TERRIER MIX</td>
            <td>Cairn TerrierRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-SHIH TZU MIX</td>
            <td>Cairn TerrierShih Tzu Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-SMOOTH FOX TERRIER MIX</td>
            <td>Cairn TerrierSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-WEST HIGHLAND WHITE TERRIER MIX</td>
            <td>Cairn TerrierWest Highland White Terrier Mix</td>
        </tr>
        <tr>
            <td>CAIRN TERRIER-YORKSHIRE TERRIER MIX</td>
            <td>Cairn TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CANAAN DOG</td>
            <td>Canaan Dog</td>
        </tr>
        <tr>
            <td>CANAAN DOG- MIX</td>
            <td>Canaan Dog Mix</td>
        </tr>
        <tr>
            <td>CANE CORSO</td>
            <td>Cane Corso</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI</td>
            <td>Cardigan Welsh Corgi</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-AMERICAN ESKIMO DOG MIX</td>
            <td>Cardigan Welsh CorgiAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Cardigan Welsh CorgiAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Cardigan Welsh CorgiAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Cardigan Welsh CorgiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-AUSTRALIAN SHEPHERD MIX</td>
            <td>Cardigan Welsh CorgiAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-BEAGLE MIX</td>
            <td>Cardigan Welsh CorgiBeagle Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-CAIRN TERRIER MIX</td>
            <td>Cardigan Welsh CorgiCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-CATAHOULA LEOPARD DOG MIX</td>
            <td>Cardigan Welsh CorgiCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-GERMAN SHEPHERD DOG MIX</td>
            <td>Cardigan Welsh CorgiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-LABRADOR RETRIEVER MIX</td>
            <td>Cardigan Welsh CorgiLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-LANCASHIRE HEELER MIX</td>
            <td>Cardigan Welsh CorgiLancashire Heeler Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-POMERANIAN MIX</td>
            <td>Cardigan Welsh CorgiPomeranian Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-RUSSELL TERRIER MIX</td>
            <td>Cardigan Welsh CorgiRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>CARDIGAN WELSH CORGI-YORKSHIRE TERRIER MIX</td>
            <td>Cardigan Welsh CorgiYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG</td>
            <td>Catahoula Leopard Dog</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG- MIX</td>
            <td>Catahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-AMERICAN LEOPARD HOUND MIX</td>
            <td>Catahoula Leopard DogAmerican Leopard Hound Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Catahoula Leopard DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Catahoula Leopard DogAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-AUSTRALIAN SHEPHERD MIX</td>
            <td>Catahoula Leopard DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-BLUETICK COONHOUND MIX</td>
            <td>Catahoula Leopard DogBluetick Coonhound Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-BORDER COLLIE MIX</td>
            <td>Catahoula Leopard DogBorder Collie Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-BOXER MIX</td>
            <td>Catahoula Leopard DogBoxer Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-GERMAN SHEPHERD DOG MIX</td>
            <td>Catahoula Leopard DogGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-LABRADOR RETRIEVER MIX</td>
            <td>Catahoula Leopard DogLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-PLOTT MIX</td>
            <td>Catahoula Leopard DogPlott Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-POINTER MIX</td>
            <td>Catahoula Leopard DogPointer Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-ROTTWEILER MIX</td>
            <td>Catahoula Leopard DogRottweiler Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-SHETLAND SHEEPDOG MIX</td>
            <td>Catahoula Leopard DogShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>CATAHOULA LEOPARD DOG-SIBERIAN HUSKY MIX</td>
            <td>Catahoula Leopard DogSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>CAUCASIAN OVCHARKA</td>
            <td>Caucasian Ovcharka</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL</td>
            <td>Cavalier King Charles Spaniel</td>
        </tr>
        <tr>
            <td>-CAVALIER KING CHARLES SPANIEL MIX</td>
            <td>Cavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-AUSTRALIAN SHEPHERD MIX</td>
            <td>Cavalier King Charles SpanielAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-BEAGLE MIX</td>
            <td>Cavalier King Charles SpanielBeagle Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-BICHON FRISE MIX</td>
            <td>Cavalier King Charles SpanielBichon Frise Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-COCKER SPANIEL MIX</td>
            <td>Cavalier King Charles SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-COTON DE TULEAR MIX</td>
            <td>Cavalier King Charles SpanielCoton de Tulear Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>Cavalier King Charles SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-MALTESE MIX</td>
            <td>Cavalier King Charles SpanielMaltese Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-PAPILLON MIX</td>
            <td>Cavalier King Charles SpanielPapillon Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-PEKINGESE MIX</td>
            <td>Cavalier King Charles SpanielPekingese Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-POMERANIAN MIX</td>
            <td>Cavalier King Charles SpanielPomeranian Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-POODLE MIX</td>
            <td>Cavalier King Charles SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-SHIH TZU MIX</td>
            <td>Cavalier King Charles SpanielShih Tzu Mix</td>
        </tr>
        <tr>
            <td>CAVALIER KING CHARLES SPANIEL-STANDARD POODLE MIX</td>
            <td>Cavalier King Charles SpanielStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>CENTRAL ASIAN SHEPHERD DOG</td>
            <td>Central Asian Shepherd Dog</td>
        </tr>
        <tr>
            <td>CENTRAL ASIAN SHEPHERD DOG-GOLDEN RETRIEVER MIX</td>
            <td>Central Asian Shepherd DogGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>CESKY TERRIER</td>
            <td>Cesky Terrier</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER</td>
            <td>Chesapeake Bay Retriever</td>
        </tr>
        <tr>
            <td>-CHESAPEAKE BAY RETRIEVER MIX</td>
            <td>Chesapeake Bay Retriever Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Chesapeake Bay RetrieverAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-BEAGLE MIX</td>
            <td>Chesapeake Bay RetrieverBeagle Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-GERMAN SHEPHERD DOG MIX</td>
            <td>Chesapeake Bay RetrieverGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-LABRADOR RETRIEVER MIX</td>
            <td>Chesapeake Bay RetrieverLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-SHIH TZU MIX</td>
            <td>Chesapeake Bay RetrieverShih Tzu Mix</td>
        </tr>
        <tr>
            <td>CHESAPEAKE BAY RETRIEVER-SIBERIAN HUSKY MIX</td>
            <td>Chesapeake Bay RetrieverSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA</td>
            <td>Chihuahua</td>
        </tr>
        <tr>
            <td>-CHIHUAHUA MIX</td>
            <td>Chihuahua Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA- MIX</td>
            <td>Chihuahua Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-AIREDALE TERRIER MIX</td>
            <td>ChihuahuaAiredale Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-AMERICAN PIT BULL TERRIER MIX</td>
            <td>ChihuahuaAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>ChihuahuaAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-AMERICAN WATER SPANIEL MIX</td>
            <td>ChihuahuaAmerican Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-AUSTRALIAN TERRIER MIX</td>
            <td>ChihuahuaAustralian Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-BEAGLE MIX</td>
            <td>ChihuahuaBeagle Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-BICHON FRISE MIX</td>
            <td>ChihuahuaBichon Frise Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-BOSTON TERRIER MIX</td>
            <td>ChihuahuaBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-CAIRN TERRIER MIX</td>
            <td>ChihuahuaCairn Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-CARDIGAN WELSH CORGI MIX</td>
            <td>ChihuahuaCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-CHINESE CRESTED MIX</td>
            <td>ChihuahuaChinese Crested Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-COCKER SPANIEL MIX</td>
            <td>ChihuahuaCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-DACHSHUND MIX</td>
            <td>ChihuahuaDachshund Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-DOBERMAN PINSCHER MIX</td>
            <td>ChihuahuaDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-GOLDEN RETRIEVER MIX</td>
            <td>ChihuahuaGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-ITALIAN GREYHOUND MIX</td>
            <td>ChihuahuaItalian Greyhound Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-JACK RUSSELL TERRIER MIX</td>
            <td>ChihuahuaJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-JAPANESE CHIN MIX</td>
            <td>ChihuahuaJapanese Chin Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-LABRADOR RETRIEVER MIX</td>
            <td>ChihuahuaLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-LHASA APSO MIX</td>
            <td>ChihuahuaLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-MALTESE MIX</td>
            <td>ChihuahuaMaltese Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-MANCHESTER TERRIER MIX</td>
            <td>ChihuahuaManchester Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-MINIATURE AUSTRALIAN SHEPHERD MIX</td>
            <td>ChihuahuaMiniature Australian Shepherd Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-MINIATURE PINSCHER MIX</td>
            <td>ChihuahuaMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-MINIATURE SCHNAUZER MIX</td>
            <td>ChihuahuaMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-NORWICH TERRIER MIX</td>
            <td>ChihuahuaNorwich Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-PAPILLON MIX</td>
            <td>ChihuahuaPapillon Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-PARSON RUSSELL TERRIER MIX</td>
            <td>ChihuahuaParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-PEKINGESE MIX</td>
            <td>ChihuahuaPekingese Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-PEMBROKE WELSH CORGI MIX</td>
            <td>ChihuahuaPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-POMERANIAN MIX</td>
            <td>ChihuahuaPomeranian Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-POODLE MIX</td>
            <td>ChihuahuaPoodle Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-PUG MIX</td>
            <td>ChihuahuaPug Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-RAT TERRIER MIX</td>
            <td>ChihuahuaRat Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-RUSSELL TERRIER MIX</td>
            <td>ChihuahuaRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-SCHIPPERKE MIX</td>
            <td>ChihuahuaSchipperke Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-SHIBA INU MIX</td>
            <td>ChihuahuaShiba Inu Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-SHIH TZU MIX</td>
            <td>ChihuahuaShih Tzu Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-SMOOTH FOX TERRIER MIX</td>
            <td>ChihuahuaSmooth Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-TOY FOX TERRIER MIX</td>
            <td>ChihuahuaToy Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-WHIPPET MIX</td>
            <td>ChihuahuaWhippet Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-WIRE FOX TERRIER MIX</td>
            <td>ChihuahuaWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-XOLOITZCUINTLI MIX</td>
            <td>ChihuahuaXoloitzcuintli Mix</td>
        </tr>
        <tr>
            <td>CHIHUAHUA-YORKSHIRE TERRIER MIX</td>
            <td>ChihuahuaYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED</td>
            <td>Chinese Crested</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-CHIHUAHUA MIX</td>
            <td>Chinese CrestedChihuahua Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-JACK RUSSELL TERRIER MIX</td>
            <td>Chinese CrestedJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-LHASA APSO MIX</td>
            <td>Chinese CrestedLhasa Apso Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-MALTESE MIX</td>
            <td>Chinese CrestedMaltese Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-PAPILLON MIX</td>
            <td>Chinese CrestedPapillon Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-POODLE MIX</td>
            <td>Chinese CrestedPoodle Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-PUG MIX</td>
            <td>Chinese CrestedPug Mix</td>
        </tr>
        <tr>
            <td>CHINESE CRESTED-RUSSELL TERRIER MIX</td>
            <td>Chinese CrestedRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI</td>
            <td>Chinese SharPei</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI- MIX</td>
            <td>Chinese SharPei Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Chinese SharPeiAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-AUSTRALIAN CATTLE DOG MIX</td>
            <td>Chinese SharPeiAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-BASSET HOUND MIX</td>
            <td>Chinese SharPeiBasset Hound Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-BOERBOEL MIX</td>
            <td>Chinese SharPeiBoerboel Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-COCKER SPANIEL MIX</td>
            <td>Chinese SharPeiCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-GERMAN SHEPHERD DOG MIX</td>
            <td>Chinese SharPeiGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-GREAT DANE MIX</td>
            <td>Chinese SharPeiGreat Dane Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-LABRADOR RETRIEVER MIX</td>
            <td>Chinese SharPeiLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-PUG MIX</td>
            <td>Chinese SharPeiPug Mix</td>
        </tr>
        <tr>
            <td>CHINESE SHAR-PEI-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>Chinese SharPeiStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CHINOOK</td>
            <td>Chinook</td>
        </tr>
        <tr>
            <td>CHINOOK-GERMAN SHEPHERD DOG MIX</td>
            <td>ChinookGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW</td>
            <td>Chow Chow</td>
        </tr>
        <tr>
            <td>CHOW CHOW-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Chow ChowAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-AUSTRALIAN SHEPHERD MIX</td>
            <td>Chow ChowAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-CATAHOULA LEOPARD DOG MIX</td>
            <td>Chow ChowCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-COCKER SPANIEL MIX</td>
            <td>Chow ChowCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-COLLIE MIX</td>
            <td>Chow ChowCollie Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-GERMAN SHEPHERD DOG MIX</td>
            <td>Chow ChowGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-GOLDEN RETRIEVER MIX</td>
            <td>Chow ChowGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-KEESHOND MIX</td>
            <td>Chow ChowKeeshond Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-LABRADOR RETRIEVER MIX</td>
            <td>Chow ChowLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-NEWFOUNDLAND MIX</td>
            <td>Chow ChowNewfoundland Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-NORFOLK TERRIER MIX</td>
            <td>Chow ChowNorfolk Terrier Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-PEMBROKE WELSH CORGI MIX</td>
            <td>Chow ChowPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-POODLE MIX</td>
            <td>Chow ChowPoodle Mix</td>
        </tr>
        <tr>
            <td>CHOW CHOW-ROTTWEILER MIX</td>
            <td>Chow ChowRottweiler Mix</td>
        </tr>
        <tr>
            <td>CIRNECO DELL&quot;ETNA</td>
            <td>Cirneco dell&quot;Etna</td>
        </tr>
        <tr>
            <td>CLUMBER SPANIEL</td>
            <td>Clumber Spaniel</td>
        </tr>
        <tr>
            <td>CLUMBER SPANIEL-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>Clumber SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>COCKAPOO</td>
            <td>Cockapoo</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL</td>
            <td>Cocker Spaniel</td>
        </tr>
        <tr>
            <td>-COCKER SPANIEL MIX</td>
            <td>Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-BICHON FRISE MIX</td>
            <td>Cocker SpanielBichon Frise Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-BOXER MIX</td>
            <td>Cocker SpanielBoxer Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-CAVALIER KING CHARLES SPANIEL MIX</td>
            <td>Cocker SpanielCavalier King Charles Spaniel Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-CHOW CHOW MIX</td>
            <td>Cocker SpanielChow Chow Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-DACHSHUND MIX</td>
            <td>Cocker SpanielDachshund Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-DOBERMAN PINSCHER MIX</td>
            <td>Cocker SpanielDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-ENGLISH COCKER SPANIEL MIX</td>
            <td>Cocker SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>Cocker SpanielEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-GOLDEN RETRIEVER MIX</td>
            <td>Cocker SpanielGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-LABRADOR RETRIEVER MIX</td>
            <td>Cocker SpanielLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-MALTESE MIX</td>
            <td>Cocker SpanielMaltese Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-MINIATURE PINSCHER MIX</td>
            <td>Cocker SpanielMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-MINIATURE SCHNAUZER MIX</td>
            <td>Cocker SpanielMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-PEKINGESE MIX</td>
            <td>Cocker SpanielPekingese Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-POMERANIAN MIX</td>
            <td>Cocker SpanielPomeranian Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-POODLE MIX</td>
            <td>Cocker SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-PUG MIX</td>
            <td>Cocker SpanielPug Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-RAT TERRIER MIX</td>
            <td>Cocker SpanielRat Terrier Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-SHETLAND SHEEPDOG MIX</td>
            <td>Cocker SpanielShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-SHIH TZU MIX</td>
            <td>Cocker SpanielShih Tzu Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-STANDARD SCHNAUZER MIX</td>
            <td>Cocker SpanielStandard Schnauzer Mix</td>
        </tr>
        <tr>
            <td>COCKER SPANIEL-TIBETAN SPANIEL MIX</td>
            <td>Cocker SpanielTibetan Spaniel Mix</td>
        </tr>
        <tr>
            <td>COLLIE</td>
            <td>Collie</td>
        </tr>
        <tr>
            <td>-COLLIE MIX</td>
            <td>Collie Mix</td>
        </tr>
        <tr>
            <td>COLLIE- MIX</td>
            <td>Collie Mix</td>
        </tr>
        <tr>
            <td>COLLIE-AMERICAN FOXHOUND MIX</td>
            <td>CollieAmerican Foxhound Mix</td>
        </tr>
        <tr>
            <td>COLLIE-ANATOLIAN SHEPHERD DOG MIX</td>
            <td>CollieAnatolian Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>COLLIE-AUSTRALIAN CATTLE DOG MIX</td>
            <td>CollieAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>COLLIE-BELGIAN MALINOIS MIX</td>
            <td>CollieBelgian Malinois Mix</td>
        </tr>
        <tr>
            <td>COLLIE-BOXER MIX</td>
            <td>CollieBoxer Mix</td>
        </tr>
        <tr>
            <td>COLLIE-GERMAN SHEPHERD DOG MIX</td>
            <td>CollieGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>COLLIE-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>CollieGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>COLLIE-GOLDEN RETRIEVER MIX</td>
            <td>CollieGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>COLLIE-LABRADOR RETRIEVER MIX</td>
            <td>CollieLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>COLLIE-SHETLAND SHEEPDOG MIX</td>
            <td>CollieShetland Sheepdog Mix</td>
        </tr>
        <tr>
            <td>COTON DE TULEAR</td>
            <td>Coton de Tulear</td>
        </tr>
        <tr>
            <td>COTON DE TULEAR-CHOW CHOW MIX</td>
            <td>Coton de TulearChow Chow Mix</td>
        </tr>
        <tr>
            <td>COTON DE TULEAR-POODLE MIX</td>
            <td>Coton de TulearPoodle Mix</td>
        </tr>
        <tr>
            <td>CURLY-COATED RETRIEVER</td>
            <td>CurlyCoated Retriever</td>
        </tr>
        <tr>
            <td>CZECHOSLOVAKIAN VLCAK</td>
            <td>Czechoslovakian Vlcak</td>
        </tr>
        <tr>
            <td>DACHSHUND</td>
            <td>Dachshund</td>
        </tr>
        <tr>
            <td>DACHSHUND- MIX</td>
            <td>Dachshund Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-AMERICAN PIT BULL TERRIER MIX</td>
            <td>DachshundAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>DachshundAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-BASSET HOUND MIX</td>
            <td>DachshundBasset Hound Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-BEAGLE MIX</td>
            <td>DachshundBeagle Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-BICHON FRISE MIX</td>
            <td>DachshundBichon Frise Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-BLACK RUSSIAN TERRIER MIX</td>
            <td>DachshundBlack Russian Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-BOSTON TERRIER MIX</td>
            <td>DachshundBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-CARDIGAN WELSH CORGI MIX</td>
            <td>DachshundCardigan Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-CHIHUAHUA MIX</td>
            <td>DachshundChihuahua Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-COCKER SPANIEL MIX</td>
            <td>DachshundCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-DOBERMAN PINSCHER MIX</td>
            <td>DachshundDoberman Pinscher Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-FLAT-COATED RETRIEVER MIX</td>
            <td>DachshundFlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-FRENCH BULLDOG MIX</td>
            <td>DachshundFrench Bulldog Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-GERMAN PINSCHER MIX</td>
            <td>DachshundGerman Pinscher Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-GERMAN SHEPHERD DOG MIX</td>
            <td>DachshundGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>DachshundGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-GLEN OF IMAAL TERRIER MIX</td>
            <td>DachshundGlen of Imaal Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-GOLDEN RETRIEVER MIX</td>
            <td>DachshundGolden Retriever Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-ITALIAN GREYHOUND MIX</td>
            <td>DachshundItalian Greyhound Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-JACK RUSSELL TERRIER MIX</td>
            <td>DachshundJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-LABRADOR RETRIEVER MIX</td>
            <td>DachshundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-MALTESE MIX</td>
            <td>DachshundMaltese Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-MINIATURE PINSCHER MIX</td>
            <td>DachshundMiniature Pinscher Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-MINIATURE SCHNAUZER MIX</td>
            <td>DachshundMiniature Schnauzer Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-PARSON RUSSELL TERRIER MIX</td>
            <td>DachshundParson Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-PEMBROKE WELSH CORGI MIX</td>
            <td>DachshundPembroke Welsh Corgi Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-POMERANIAN MIX</td>
            <td>DachshundPomeranian Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-POODLE MIX</td>
            <td>DachshundPoodle Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-PUG MIX</td>
            <td>DachshundPug Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-RAT TERRIER MIX</td>
            <td>DachshundRat Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-RUSSELL TERRIER MIX</td>
            <td>DachshundRussell Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-SCOTTISH TERRIER MIX</td>
            <td>DachshundScottish Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-SHIH TZU MIX</td>
            <td>DachshundShih Tzu Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>DachshundStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-WIRE FOX TERRIER MIX</td>
            <td>DachshundWire Fox Terrier Mix</td>
        </tr>
        <tr>
            <td>DACHSHUND-YORKSHIRE TERRIER MIX</td>
            <td>DachshundYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN</td>
            <td>Dalmatian</td>
        </tr>
        <tr>
            <td>DALMATIAN-AMERICAN PIT BULL TERRIER MIX</td>
            <td>DalmatianAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-AUSTRALIAN CATTLE DOG MIX</td>
            <td>DalmatianAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-AUSTRALIAN SHEPHERD MIX</td>
            <td>DalmatianAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-BEAGLE MIX</td>
            <td>DalmatianBeagle Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-BORDER COLLIE MIX</td>
            <td>DalmatianBorder Collie Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-GREAT PYRENEES MIX</td>
            <td>DalmatianGreat Pyrenees Mix</td>
        </tr>
        <tr>
            <td>DALMATIAN-LABRADOR RETRIEVER MIX</td>
            <td>DalmatianLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>DANDIE DINMONT TERRIER</td>
            <td>Dandie Dinmont Terrier</td>
        </tr>
        <tr>
            <td>DANDIE DINMONT TERRIER-YORKSHIRE TERRIER MIX</td>
            <td>Dandie Dinmont TerrierYorkshire Terrier Mix</td>
        </tr>
        <tr>
            <td>DANISH-SWEDISH FARMDOG</td>
            <td>DanishSwedish Farmdog</td>
        </tr>
        <tr>
            <td>DANISH-SWEDISH FARMDOG-CZECHOSLOVAKIAN VLCAK MIX</td>
            <td>DanishSwedish FarmdogCzechoslovakian Vlcak Mix</td>
        </tr>
        <tr>
            <td>DEUTSCHER WACHTELHUND</td>
            <td>Deutscher Wachtelhund</td>
        </tr>
        <tr>
            <td>DEUTSCHER WACHTELHUND- MIX</td>
            <td>Deutscher Wachtelhund Mix</td>
        </tr>
        <tr>
            <td>DEUTSCHER WACHTELHUND-NEWFOUNDLAND MIX</td>
            <td>Deutscher WachtelhundNewfoundland Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER</td>
            <td>Doberman Pinscher</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>Doberman PinscherAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-BEAGLE MIX</td>
            <td>Doberman PinscherBeagle Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-BEAUCERON MIX</td>
            <td>Doberman PinscherBeauceron Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-BLACK AND TAN COONHOUND MIX</td>
            <td>Doberman PinscherBlack and Tan Coonhound Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-BOXER MIX</td>
            <td>Doberman PinscherBoxer Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-CATAHOULA LEOPARD DOG MIX</td>
            <td>Doberman PinscherCatahoula Leopard Dog Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-DALMATIAN MIX</td>
            <td>Doberman PinscherDalmatian Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-GERMAN SHEPHERD DOG MIX</td>
            <td>Doberman PinscherGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-GREYHOUND MIX</td>
            <td>Doberman PinscherGreyhound Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-LABRADOR RETRIEVER MIX</td>
            <td>Doberman PinscherLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-POODLE MIX</td>
            <td>Doberman PinscherPoodle Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-PUG MIX</td>
            <td>Doberman PinscherPug Mix</td>
        </tr>
        <tr>
            <td>DOBERMAN PINSCHER-ROTTWEILER MIX</td>
            <td>Doberman PinscherRottweiler Mix</td>
        </tr>
        <tr>
            <td>DOGO ARGENTINO</td>
            <td>Dogo Argentino</td>
        </tr>
        <tr>
            <td>DOGO ARGENTINO-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Dogo ArgentinoAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>DOGUE DE BORDEAUX</td>
            <td>Dogue de Bordeaux</td>
        </tr>
        <tr>
            <td>DOGUE DE BORDEAUX-AMERICAN PIT BULL TERRIER MIX</td>
            <td>Dogue de BordeauxAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>DOGUE DE BORDEAUX-BOXER MIX</td>
            <td>Dogue de BordeauxBoxer Mix</td>
        </tr>
        <tr>
            <td>DOGUE DE BORDEAUX-LABRADOR RETRIEVER MIX</td>
            <td>Dogue de BordeauxLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>DRENTSCHE PATRIJSHOND</td>
            <td>Drentsche Patrijshond</td>
        </tr>
        <tr>
            <td>DUTCH SHEPHERD</td>
            <td>Dutch Shepherd</td>
        </tr>
        <tr>
            <td>DUTCH SHEPHERD-APPENZELLER SENNENHUNDE MIX</td>
            <td>Dutch ShepherdAppenzeller Sennenhunde Mix</td>
        </tr>
        <tr>
            <td>DUTCH SHEPHERD-LABRADOR RETRIEVER MIX</td>
            <td>Dutch ShepherdLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>DUTCH SHEPHERD-SIBERIAN HUSKY MIX</td>
            <td>Dutch ShepherdSiberian Husky Mix</td>
        </tr>
        <tr>
            <td>ENGLISH COCKER SPANIEL</td>
            <td>English Cocker Spaniel</td>
        </tr>
        <tr>
            <td>ENGLISH COCKER SPANIEL-COCKER SPANIEL MIX</td>
            <td>English Cocker SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>ENGLISH COCKER SPANIEL-POODLE MIX</td>
            <td>English Cocker SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>ENGLISH FOXHOUND</td>
            <td>English Foxhound</td>
        </tr>
        <tr>
            <td>ENGLISH FOXHOUND-LABRADOR RETRIEVER MIX</td>
            <td>English FoxhoundLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER</td>
            <td>English Setter</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER- MIX</td>
            <td>English Setter Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-BEAGLE MIX</td>
            <td>English SetterBeagle Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-BORDER COLLIE MIX</td>
            <td>English SetterBorder Collie Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-BRITTANY MIX</td>
            <td>English SetterBrittany Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-DALMATIAN MIX</td>
            <td>English SetterDalmatian Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-ENGLISH SPRINGER SPANIEL MIX</td>
            <td>English SetterEnglish Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-LABRADOR RETRIEVER MIX</td>
            <td>English SetterLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SETTER-POINTER MIX</td>
            <td>English SetterPointer Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL</td>
            <td>English Springer Spaniel</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL- MIX</td>
            <td>English Springer Spaniel Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-AUSTRALIAN CATTLE DOG MIX</td>
            <td>English Springer SpanielAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-BORDER COLLIE MIX</td>
            <td>English Springer SpanielBorder Collie Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-COCKER SPANIEL MIX</td>
            <td>English Springer SpanielCocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-DALMATIAN MIX</td>
            <td>English Springer SpanielDalmatian Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-ENGLISH COCKER SPANIEL MIX</td>
            <td>English Springer SpanielEnglish Cocker Spaniel Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-GERMAN SHEPHERD DOG MIX</td>
            <td>English Springer SpanielGerman Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-JACK RUSSELL TERRIER MIX</td>
            <td>English Springer SpanielJack Russell Terrier Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-LABRADOR RETRIEVER MIX</td>
            <td>English Springer SpanielLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-POINTER MIX</td>
            <td>English Springer SpanielPointer Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-POODLE MIX</td>
            <td>English Springer SpanielPoodle Mix</td>
        </tr>
        <tr>
            <td>ENGLISH SPRINGER SPANIEL-STANDARD POODLE MIX</td>
            <td>English Springer SpanielStandard Poodle Mix</td>
        </tr>
        <tr>
            <td>ENGLISH TOY SPANIEL</td>
            <td>English Toy Spaniel</td>
        </tr>
        <tr>
            <td>ENTLEBUCHER MOUNTAIN DOG</td>
            <td>Entlebucher Mountain Dog</td>
        </tr>
        <tr>
            <td>ESTRELA MOUNTAIN DOG</td>
            <td>Estrela Mountain Dog</td>
        </tr>
        <tr>
            <td>EURASIER</td>
            <td>Eurasier</td>
        </tr>
        <tr>
            <td>FIELD SPANIEL</td>
            <td>Field Spaniel</td>
        </tr>
        <tr>
            <td>FINNISH LAPPHUND</td>
            <td>Finnish Lapphund</td>
        </tr>
        <tr>
            <td>FINNISH SPITZ</td>
            <td>Finnish Spitz</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER</td>
            <td>FlatCoated Retriever</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER- MIX</td>
            <td>FlatCoated Retriever Mix</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER-BORDER COLLIE MIX</td>
            <td>FlatCoated RetrieverBorder Collie Mix</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER-IRISH WATER SPANIEL MIX</td>
            <td>FlatCoated RetrieverIrish Water Spaniel Mix</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER-LABRADOR RETRIEVER MIX</td>
            <td>FlatCoated RetrieverLabrador Retriever Mix</td>
        </tr>
        <tr>
            <td>FLAT-COATED RETRIEVER-PORTUGUESE WATER DOG MIX</td>
            <td>FlatCoated RetrieverPortuguese Water Dog Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG</td>
            <td>French Bulldog</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-BOSTON TERRIER MIX</td>
            <td>French BulldogBoston Terrier Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-BULLDOG MIX</td>
            <td>French BulldogBulldog Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-HAVANESE MIX</td>
            <td>French BulldogHavanese Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-PUG MIX</td>
            <td>French BulldogPug Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-SHIH TZU MIX</td>
            <td>French BulldogShih Tzu Mix</td>
        </tr>
        <tr>
            <td>FRENCH BULLDOG-STAFFORDSHIRE BULL TERRIER MIX</td>
            <td>French BulldogStaffordshire Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>FRENCH SPANIEL</td>
            <td>French Spaniel</td>
        </tr>
        <tr>
            <td>FRENCH SPANIEL-GERMAN SHORTHAIRED POINTER MIX</td>
            <td>French SpanielGerman Shorthaired Pointer Mix</td>
        </tr>
        <tr>
            <td>GERMAN LONGHAIRED POINTER</td>
            <td>German Longhaired Pointer</td>
        </tr>
        <tr>
            <td>GERMAN LONGHAIRED POINTER-POINTER MIX</td>
            <td>German Longhaired PointerPointer Mix</td>
        </tr>
        <tr>
            <td>GERMAN PINSCHER</td>
            <td>German Pinscher</td>
        </tr>
        <tr>
            <td>GERMAN PINSCHER-WEIMARANER MIX</td>
            <td>German PinscherWeimaraner Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG</td>
            <td>German Shepherd Dog</td>
        </tr>
        <tr>
            <td>-GERMAN SHEPHERD DOG MIX</td>
            <td>German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG- MIX</td>
            <td>German Shepherd Dog Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AKITA MIX</td>
            <td>German Shepherd DogAkita Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-ALASKAN MALAMUTE MIX</td>
            <td>German Shepherd DogAlaskan Malamute Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AMERICAN ESKIMO DOG MIX</td>
            <td>German Shepherd DogAmerican Eskimo Dog Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AMERICAN PIT BULL TERRIER MIX</td>
            <td>German Shepherd DogAmerican Pit Bull Terrier Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AMERICAN STAFFORDSHIRE TERRIER MIX</td>
            <td>German Shepherd DogAmerican Staffordshire Terrier Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AUSTRALIAN CATTLE DOG MIX</td>
            <td>German Shepherd DogAustralian Cattle Dog Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AUSTRALIAN KELPIE MIX</td>
            <td>German Shepherd DogAustralian Kelpie Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-AUSTRALIAN SHEPHERD MIX</td>
            <td>German Shepherd DogAustralian Shepherd Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-BASENJI MIX</td>
            <td>German Shepherd DogBasenji Mix</td>
        </tr>
        <tr>
            <td>GERMAN SHEPHERD DOG-BASSET HOUND MIX</td>
            <td>German Shepherd DogBasset Hound Mix</td>
        </tr>
    </table>
    <span style="font-style:italic;text-align:center;">2006 rows, truncated to displaylimit of 1000</span>



**Practice any other queries you want to try below!**

