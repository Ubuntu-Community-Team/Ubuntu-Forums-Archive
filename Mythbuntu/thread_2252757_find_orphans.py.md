---
title: "find_orphans.py"
date: 2014-11-14
forum: Mythbuntu
---

### Post by deanie44 on 2014-11-14
Can find_orphans.py be used in mythtv 0,27?   I am trying to run it from the maintenance folder on ubuntu and it says it doesn't exist.
I know the file exists for i created the folder.  Is it because I am using a x64 system instead of x32?  I am confused.  Any suggestions will be appreciated, deanie44

---

### Post by aelfric55 on 2014-11-14
The wiki page for it doesn't list it as supported for 0.27, but it works perfectly in 0.27.  I use it probably once a week or so.

Since you didn't include the actual command you were using or the resulting error message verbatim, I'm only guessing that either you didn't invoke the command for the script properly (using the full path to it, or ./ if you're already in the correct directory), or possibly you didn't make the find_orphans.py script executable. Or it's not actually installed where you think it is.

---

### Post by deanie44 on 2014-11-14
Hi aelfric55.  I installed in /home/deanie56/Find_orphans.py.  I tried to used the instructions from [http://mylinuxramblings.wordpress.com/2013/10/12/useful-utilities-for-managing-mythtv-and-mythbuntu/](http://mylinuxramblings.wordpress.com/2013/10/12/useful-utilities-for-managing-mythtv-and-mythbuntu/),  I could not get it the work,  In the terminal I would receive an error message stating that the file cannot be found.  Is home the wrong directory,  Also I copied and paste tha script for I had problems downloading it from mythwikiscripts.  The actual command that i used is **chmod 755 Find_orphans.py and ****./Find_orphans.py, which lead to the "file or directory does not exist."  **Any assistance that you can give me will be appreciated.  Thank you deanie44

---

### Post by aelfric55 on 2014-11-14
I suspect that the file is actually named "find_orphans.py" and not "Find_orphans.py" But check --since you're already in your /home/deanie56 directory, ```
ls *orphans*
``` will find every file in that directory with "orphans" in the name. Assuming that the filename actually is find_orphans.py then ```
./find_orphans.py
``` or ```
/home/deanie56/find_orphans.py
``` should get the job done.

---

### Post by deanie44 on 2014-11-14
I am sorry to say the three commands you gave me did not work,  I am confused.  I do not understand why It is not working.  here is the outcome of the terminal:

deanie56@deanie56-Inspiron-560:~$ ls *orphans*
Find_orphans.py
deanie56@deanie56-Inspiron-560:~$ ./find_orphans.py
bash: ./find_orphans.py: No such file or directory
deanie56@deanie56-Inspiron-560:~$ ./Find_orphans.py
./Find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./Find_orphans.py: line 8: import: command not found
./Find_orphans.py: line 9: import: command not found
./Find_orphans.py: line 11: syntax error near unexpected token `('
./Find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ /home/deanie56/Find_orphans.py
/home/deanie56/Find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
/home/deanie56/Find_orphans.py: line 8: import: command not found
/home/deanie56/Find_orphans.py: line 9: import: command not found
/home/deanie56/Find_orphans.py: line 11: syntax error near unexpected token `('
/home/deanie56/Find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ 
 Thanks again.  deanie44

---

### Post by aelfric55 on 2014-11-14
It looks like you have basically the version of the script from the wiki [https://www.mythtv.org/wiki/Find_orphans.py](https://www.mythtv.org/wiki/Find_orphans.py) It also looks like your copy has the intended filename "find_orphans.py" erroneously imbedded as the first command in the first line of the script itself, which is why you're getting that odd line 1 error "./Find_orphans.py: line 1: find_orphans.py: command not found"

But beyond that the two failed 'import's after the two failed 'from's would seem to indicate that there's something missing or not properly installed from your python bindings for mythtv or from the python installation itself. 

I simply don't know enough about python to be able to help with that, particularly on Ubuntu.

---

### Post by dannyboy79 on 2014-11-14
rename the python script to 
```
find_orphans.py
```
and you should be good to go.

---

### Post by Lester_Burnham on 2014-11-15
If the above doesn't work after renaming.
Try
```
python find_orphans.py
```

If that doesn't work, check if the file is executable. (Right click, properties, last tab)

Lester

---

### Post by deanie44 on 2014-11-15
Lester_Burham, thanks for answering my post.  I renamed the file to find_orphans.py and make it executable.  The outcome in the terminal is stll the same:


deanie56@deanie56-Inspiron-560:~$ ls *orphans*
Find_orphans.py
deanie56@deanie56-Inspiron-560:~$ ./find_orphans.py
bash: ./find_orphans.py: No such file or directory
deanie56@deanie56-Inspiron-560:~$ ./Find_orphans.py
./Find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./Find_orphans.py: line 8: import: command not found
./Find_orphans.py: line 9: import: command not found
./Find_orphans.py: line 11: syntax error near unexpected token `('
./Find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ /home/deanie56/Find_orphans.py
/home/deanie56/Find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
/home/deanie56/Find_orphans.py: line 8: import: command not found
/home/deanie56/Find_orphans.py: line 9: import: command not found
/home/deanie56/Find_orphans.py: line 11: syntax error near unexpected token `('
/home/deanie56/Find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ 
 
I think the script is outdated or something  is wrong with it.  Thank you for your help.  Thanks again.  deanie44

---

### Post by khPWXxF on 2014-11-15
ok, let's try some basics here.

1.  It doesn't matter whether it's Find_orphans.py or find_orphans.py so long as you are consistent.  Confusion arises because the wiki does not allow page/article titles starting with lower case.

2.  You can find where it is with ```
locate find_orphans.py
```
3.  Once you find it, cd to the directory holding it.
4.  It needs to have both read and execute permissions.  To check and fix it do:
```
ls -l find_orphans.py
chmod 755 find_orphans.py
```
That's all lower case 'LS -L'

5.  You didn't download this in a Windows environment did you?   If so then you might have both carriage return and linefeeds  at the end of each line in the file which will cause havoc. Chop out the c/rs with:

```
cat find_orphans.py | tr -d "\r" > temp
cp temp find_orphans.py

```
6.  I have a suspicion that there is a problem in the first line of your file.  Mine says:
> #!/usr/bin/env python

If you need to change it, I like gedit.  Just remember ^s to save, ^q to quit.

7.  Finally,  execute it with:
```
./find_orphans.py
```
Hint:  You quit it with Control C.

Best wishes,
Phil

---

### Post by deanie44 on 2014-11-16
Hi.  				 				 					 						 	[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453") thanks for answering my post.  I followed you directions, but it did not work. Here is to outcome of the terminal:

deanie56@deanie56-Inspiron-560:~$ cd /usr/share/doc/mythtv-backend/contrib/maintenance
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ ls -l find_orphans.py
-rwxrwx--x 1 deanie56 deanie56 7224 Nov 13 18:02 find_orphans.py
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ chmod 755 find_orphans.py
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ cat find_orphans.py | tr -d "\r" > temp
bash: temp: Permission denied
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ cp temp find_orphans.py
cp: cannot stat &#8216;temp&#8217;: No such file or directory
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ ./find_orphans.py
./find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./find_orphans.py: line 8: import: command not found
./find_orphans.py: line 9: import: command not found
./find_orphans.py: line 11: syntax error near unexpected token `('
./find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:/usr/share/doc/mythtv-backend/contrib/maintenance$ 

Thanks again.  deanie44

---

### Post by khPWXxF on 2014-11-16
Hi Dean,
 
Sorry - forgot that if you don't have sufficient privileges on the directory things will not work without sudo.  This is more a ubuntu tutorial than a find_orphans one.  We are trying to check that permissions are right and that it looks like a bit of python. 
Let’s try it in your home directory:  The # lines are comments for you, they are not needed by ubuntu but won’t harm it.
```
#switch to home directory
cd ~

#copy find_orphans.py to home directory. ~ is shorthand for home directory.
cp /usr/share/doc/mythtv-backend/contrib/maintenance/find_orphans.py ~

#you probably won't need these steps unless it has been in a windows environment but they won't harm: 
cat find_orphans.py | tr -d "\r" > temp
cp temp find_orphans.py

#but you will need read and execute permissions: 
chmod 755 find_orphans.py

#now check that first line is '#!/usr/bin/env python by listing the start of it:
head find_orphans.py
 
#If it is then execute it.  The ./ says 'look in current directory':
./find_orphans.py

```
hth
Phil

---

### Post by deanie44 on 2014-11-16
Hi.  I believe the script is broken.  here is the outcome from the terminal:

deanie56@deanie56-Inspiron-560:~$ cp /usr/share/doc/mythtv-backend/contrib/maintenance/find_orphans.py ~
deanie56@deanie56-Inspiron-560:~$ cat find_orphans.py | tr -d "\r" > temp
deanie56@deanie56-Inspiron-560:~$ cp temp find_orphans.py
deanie56@deanie56-Inspiron-560:~$ chmod 755 find_orphans.py
deanie56@deanie56-Inspiron-560:~$ head find_orphans.py
find_orphans.py

#!/usr/bin/env python

from MythTV import MythDB, MythBE, Recorded, MythError
from socket import timeout

import os
import sys

deanie56@deanie56-Inspiron-560:~$  ./find_orphans.py
./find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./find_orphans.py: line 8: import: command not found
./find_orphans.py: line 9: import: command not found
./find_orphans.py: line 11: syntax error near unexpected token `('
./find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ cd /home/deanie56
deanie56@deanie56-Inspiron-560:~$ ./find_orphans.py
./find_orphans.py: line 1: find_orphans.py: command not found
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./find_orphans.py: line 8: import: command not found
./find_orphans.py: line 9: import: command not found
./find_orphans.py: line 11: syntax error near unexpected token `('
./find_orphans.py: line 11: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$ 

thanks again deanie44

---

### Post by khPWXxF on 2014-11-16
Your find_orphans.py file  has two spurious lines at the start.  One says 'find_orphans.py' the next is blank.
Remove them both - if you don't have a favourite editor I suggest you use 
```
gedit  find_orphans.py
```

Save with ^s, quit with ^q.

Phil

---

### Post by khPWXxF on 2014-11-17
Perhaps I should also have explained something otherwise it's all smoke and magic!

Windows uses a filename suffix to decide which application should be invoked when you click on a file.  Something.doc for word, something.jpg for a photo viewer, something.gpx for mapping/gps stuff.

Linux is quite different - it looks in the first line of the file and expects to see a line starting #! to see which application / reader to invoke.  So for a perl script you'd use
#!/usr/bin/perl

For a bash script 
#!/bin/bash

That #! line line was not found on the first line of the file so the interpreter was confused and carried on trying to make sense of the file.  Python wasn't invited to the party!

Elsewhere of course, a leading # is usually treated as a comment and ignored.
Phil

---

### Post by deanie44 on 2014-11-17
[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453")       thanki again.  I still get the same message in the terrminal.  Here's the thing--I have ubuntu-desktop on top of mythbuntu. Do you think that could be the reason the script is not working? thanks deanie44
deanie56@deanie56-Inspiron-560:~$ cd ~
deanie56@deanie56-Inspiron-560:~$ cat find_orphans.py | tr -d "\r" > temp
deanie56@deanie56-Inspiron-560:~$ cp temp find_orphans.py
deanie56@deanie56-Inspiron-560:~$ chmod 755 find_orphans.py
deanie56@deanie56-Inspiron-560:~$ head find_orphans.py

#!/usr/bin/env python
from MythTV import MythDB, MythBE, Recorded, MythError
from socket import timeout

import os
import sys

def human_size(s):
    s = float(s)
deanie56@deanie56-Inspiron-560:~$  ./find_orphans.py
from: can't read /var/mail/MythTV
from: can't read /var/mail/socket
./find_orphans.py: line 6: import: command not found
./find_orphans.py: line 7: import: command not found
./find_orphans.py: line 9: syntax error near unexpected token `('
./find_orphans.py: line 9: `def human_size(s):'
deanie56@deanie56-Inspiron-560:~$

---

### Post by khPWXxF on 2014-11-17
You can forget all the 'tr' stuff now.  I don't think that the desktop is the issue, but unless it's a transcription error you still have a blank line at the start of your file.

Display line numbers with:
```
cat -n find_orphans.py | head
```

if there is a spurious blank line no 1 then edit the file
```
gedit find_orphans.py
```

you can turn on line numbering with edit > preferences and tick line numbers box.
Put the cursor on the blank line, press 'delete'
When it looks right, control-S and control Q

Think we're nearly there!
Phil

---

### Post by deanie44 on 2014-11-17
[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453")       thanki again.  I still get the same message in the terrminal.  Here's the thing--I have ubuntu-desktop on top of mythbuntu. Do you think that could be the reason the script is not working? thanks deanie44

---

### Post by deanie44 on 2014-11-17
It works.  Thanking everyone  for your superb help!  nadine

---

