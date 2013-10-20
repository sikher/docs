# GurbaniDB SQL Dump Readme #

## Link to SQL Files ##
* Small SQL Files - http://www.sikher.com/sql/ - This is the recommended way of using GurbaniDB because you can customize what you want to include in your database. The rest of this readme is designed only for these small SQL files
* One Big SQL File - http://sourceforge.net/projects/sikher/files/Database/ - This contains the entire GurbaniDB database and is not recommended as it is _not_ customizable and some developers have experienced problems in using it

**Please note:** As of 20th of October 2013, ShabadID is now supported in GurbaniDB. Thanks to Harvinder Singh from [khojgurbani.org](http://www.khojgurbani.org) for this data. ShabadID can be found in _tblscripture_ which is part of [gurbanidb_core.sql](www.sikher.com/sql/gurbanidb_core.sql)

## Small SQL File Contents ##
* `gurbanidb_er.pdf` - This entity-relationship diagram maps all the 
primary and foreign key relationship between the tables
* `gurbanidb_core.sql` - This contains all the core gurbanidb tables and
so it should be installed first. Then you can pick and choose which
translations or transliterations to add to your database by just dropping
them in!
* In order to find a specific translation or transliteration please use the
Translation Key or Transliteration Key at the bottom of this README to find
the correct {number}:


		http://www.sikher.com/sql/translation-{number}.sql
		
	Or...

		http://www.sikher.com/sql/transliteration-{number}.sql
		
After downloading the files simply use the MySQL command-line to dump it
straight into your `tbltranslation` or `tbltransliteration` tables. If you are
unsure how to do this, it shall be explained later on in this README.

## Setup ##
1. Make sure you first know the path to your MySQL command-line. On Windows, if you have XAMPP installed this may be: `C:\xampp\mysql\bin\mysql.exe`. On Linux, this will usually be just `mysql`.
2. Make sure you know your MySQL username, password and hostname. If working locally, your hostname will usually just be `localhost`.
3. Find out the link to your PhpMyAdmin installation. Again if using XAMPP, this will usually be `http://localhost/phpmyadmin/`.

## Installing GurbaniDB using PhpMyAdmin and the MySQL command-line ##
1. Download the `gurbanidb_core.sql` file which gives you all the 
basic tables you need
2. Use `phpmyadmin` to create a new database with the collation 
`utf8_unicode_ci`. You can name the database anything you want, but a 
suggestion would be `gurbanidb`.
3. Open up a new terminal or command prompt and `cd` into the 
directory your `gurbanidb_core.sql` file is located in
4. Then run the following command in the terminal or command prompt, 
replacing the values with your MySQL connection details (and using the
path to mysql we defined earlier in the Setup):
	* `mysql` -u `username` -p`password` -h `hostname` `database` < gurbanidb_core.sql
5. Let's do a quick data integrity check. Just make sure tblscripture
has 60,403 rows in phpmyadmin. If it does, let's continue.
6. Now download the translations or transliterations you want to add to
your database from `http://www.sikher.com/sql/` and put them in the same
folder as before (where `gurbanidb_core.sql` is located).
7. Now run the same command as before, but this time inputting the new
translation/transliteration file:
	* `mysql` -u `username` -p`password` -h `hostname` `database` < translation-`{number}`.sql
	* `mysql` -u `username` -p`password` -h `hostname` `database` < transliteration-`{number}`.sql
8. Ok fantastic! Now time for another data integrity check. Please check each
transliteration or transliteration has EXACTLY 60,403 rows in phpmyadmin, so if
you have two translations, this should amount to exactly 120,806 rows.
9. Take a look at `gurbanidb_er.pdf` in order to determine how all the tables
link together
10. Success! You have installed GurbaniDB. More information on the database fields can
be found in the developer guide here:

		http://media.sikher.com/files/GurbaniDB_Cloud_Documentation.pdf

### Translation Key ###
1. Afrikaans
2. Albanian
3. Arabic
4. Belarusian
5. Bulgarian
6. Catalan
7. Chinese Simplified
8. Chinese Traditional
9. Croatian
10. Czech
11. Danish
12. Dutch
13. English
14. Estonian
15. Filipino
16. Finnish
17. French
18. Galician
19. German
20. Greek
21. Haitian
22. Hebrew
23. Hindi
24. Hungarian
25. Icelandic
26. Indonesian
27. Irish
28. Italian
29. Japanese
30. Korean
31. Latvian
32. Lithuanian
33. Macedonian
34. Malay
35. Maltese
36. Norwegian
37. Persian
38. Polish
39. Portuguese
40. Romanian
41. Russian
42. Serbian
43. Slovak
44. Slovenian
45. Spanish
46. Swahili
47. Swedish
48. Thai
49. Turkish
50. Ukrainian
51. Vietnamese
52. Welsh
53. Yiddish

### Transliteration Key ###
1. Arabic
2. Armenian
3. Bengali
4. Cyrillic
5. Devanagari
6. Georgian
7. Greek
8. Gujarati
9. Hangul
10. Hebrew
11. Hiragana
12. Jamo
13. Kannada
14. Katakana
15. Latin
16. Malayalam
17. Oryia
18. Syriac
19. Tamil
20. Telugu
21. Thaana
22. Thai

## Support ##
* Email us - info {at} sikher {dot} com
