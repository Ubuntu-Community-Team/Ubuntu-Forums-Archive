---
title: "how to login the ftp web?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by luofeiyu on 2010-09-07
please  click
[http://www.sec.gov/edgar/searchedgar/ftpusers.htm](http://www.sec.gov/edgar/searchedgar/ftpusers.htm)
it say

To retrive this file:

ftp> cd edgar
ftp> cd data/100334/
ftp> get 0000100334-06-000121.txt

in my console

pt@pt-laptop:~$ ftp [ftp://ftp.sec.gov/edgar/](ftp://ftp.sec.gov/edgar/)
ftp: [ftp://ftp.sec.gov/edgar/:](ftp://ftp.sec.gov/edgar/:) Unknown host
ftp> cd edgar
Not connected.
what is the matter?

---

### Post by MaindotC on 2010-09-07
use:```

ftp ftp.sec.gov

```
then when you are connected, cd to the edgar/ directory.

---

### Post by luofeiyu on 2010-09-07
think you,there is another problem too
ftp> dir  /edgar
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-x--x   8 1019     bin          4096 Oct  7  2004 1998
drwxr-x--x  39 1019     bin          4096 May  4 20:59 1999
drwxr-xr-x   6 1019     bin          4096 Oct  7  2004 2000
-rw-r--r--   1 1024     bin       1508388 Aug 21  2009 2009-03-23.rss.xml
lrwxrwxrwx   1 root     bin             9 Jun 19  2002 Feed -> 2000/Feed
lrwxrwxrwx   1 root     bin            13 Jun 19  2002 Oldloads -> data/oldloads
-rw-r--r--   1 root     bin          7208 Jul 10  2007 README.txt
drwxr-xr-x   2 1019     bin          4096 Oct  7  2004 Tools
drwxr-xr-x  19 1019     bin         53248 Sep  4 02:03 daily-index
drwxr-x--x 31376 1019     bin      13422592 Sep  7 10:08 data
drwxr-xr-x   2 1019     bin          4096 Aug  1 08:46 docs
drwxr-xr-x   2 1019     bin          4096 Oct  7  2004 forms
drwxr-xr-x  20 1019     bin          4096 Sep  4 02:04 full-index
lrwxrwxrwx   1 root     root           33 Oct  7  2004 index.htm -> /usr/local/web/index.nobrowse.htm
drwxr-xr-x   2 1024     bin          4096 Sep  1 05:00 monthly
-rw-r--r--   1 1024     106        860588 Sep  7 10:40 usgaap.rss.xml
-rw-r--r--   1 1024     106        437347 Aug 13 01:50 usgaap.rss.xml.20100812
drwx------  24 1024     bin          4096 May  4  2009 vprr
-rw-r--r--   1 1024     106         88759 Sep  7 10:40 xbrl-rr-vfp.rss.xml
-rw-r--r--   1 1024     bin           906 Sep  7 10:40 xbrl-rr.rss.xml
lrwxrwxrwx   1 root     root           44 Jun 10  2009 xbrl.html -> /usr/local/web/info/edgar/ednews/xbrlrss.htm
-rw-r--r--   1 root     bin      79934154 Mar 24  2009 xbrldata.tar.gz
-rw-r--r--   1 root     bin      78763738 Mar 24  2009 xbrldata.zip
-rw-r--r--   1 1024     106        837794 Sep  7 10:40 xbrlrss.all.xml
-rw-r--r--   1 1024     106        425863 Aug 13 01:50 xbrlrss.all.xml.20100812
-rw-r--r--   1 1024     bin          5816 Apr 17  2009 xbrlrss.idea.xml
-rw-r--r--   1 1024     bin         92840 Apr  8 00:50 xbrlrss.risk-return.xml
-rw-r--r--   1 1024     106         92840 Apr  8 00:50 xbrlrss.risk-return.xml.20100812
-rw-r--r--   1 1024     bin           816 Apr  8 00:50 xbrlrss.rr2008.xml
-rw-r--r--   1 1024     106           816 Apr  8 00:50 xbrlrss.rr2008.xml.20100812
-rw-r--r--   1 1024     106        648960 Sep  7 10:40 xbrlrss.xml
-rw-r--r--   1 1024     106        359838 Aug 13 01:50 xbrlrss.xml.20100812
226 Transfer complete
ftp> get  /edgar/README.txt
local: ./edgar/README.txt remote: /edgar/README.txt
local: ./edgar/README.txt: No such file or directory
what is matter with  get  /edgar/README.txt

---

### Post by MaindotC on 2010-09-07
I'm not sure.  Move to the /edgar directory and then try to get the file.  Since you are connecting to a server run by a U. S. federal agency I'm assuming you are an employee or contractor of theirs.  Do you not have an IT staff at the SEC that you can contact?  There's even a page [for EDGAR users](http://www.sec.gov/edgar.shtml).

---

### Post by bab1 on 2010-09-07
> **strAlan said:**
> I'm not sure.  Move to the /edgar directory and then try to get the file.  Since you are connecting to a server run by a U. S. federal agency I'm assuming you are an employee or contractor of theirs.  Do you not have an IT staff at the SEC that you can contact?  There's even a page [for EDGAR users](http://www.sec.gov/edgar.shtml).

This is public information.  This is an anonymous FTP server run by the SEC.  

[QUOTE=luofeiyu]ftp> get /edgar/README.txt[/QUOTE]
The FTP command is incorrect here.  Once you are in the directory you only ned to "get" the file.  like this ```
get README.txt
```

Edit: Before you use the FTP command make sure you are at the directory you want to store the files you are downloading.  The command line FTP app will not ask you where you would like the files to go.  It assumes you want the data in the directory you are presently in.

This would be far easier using a graphical FTP client if you just want a few files.

---

### Post by luofeiyu on 2010-09-07
think for your help.
i am an investor in china, want to buy some usa stock,first of all , i need some public material to value the company.
when i use command in my console:
 dir  /edgar/data/1000045/  
i can get output such as:
lrwxrwxrwx   1 1019     bin            55 Jan 25  2006 000114420406002619 -> /usr/local/ftp/edgar/data/1000045/06/000114420406002619
lrwxrwxrwx   1 1019     bin            55 Feb  1  2006 000114420406003517 -> /usr/local/ftp/edgar/data/1000045/06/000114420406003517
lrwxrwxrwx   1 1019     bin            55 Sep 27  2006 000114420406004407 -> /usr/local/ftp/edgar/data/1000045/06/000114420406004407
lrwxrwxrwx   1 1019     bin            55 Feb 14  2006 000114420406005708 -> /usr/local/ftp/edgar/data/1000045/06/000114420406005708
lrwxrwxrwx   1 1019     bin            55 Feb 15  2006 000114420406006463 -> /usr/local/ftp/edgar/data/1000045/06/000114420406006463
lrwxrwxrwx   1 1019     bin            55 Feb 22  2006 000114420406007252 -> /usr/local/ftp/edgar/data/1000045/06/000114420406007252
lrwxrwxrwx   1 1019     bin            55 Apr 26  2006 000114420406016833 -> /usr/local/ftp/edgar/data/1000045/06/000114420406016833
lrwxrwxrwx   1 1019     bin            55 May  8  2006 000114420406018820 -> /usr/local/ftp/edgar/data/1000045/06/000114420406018820
lrwxrwxrwx   1 1019     bin            55 May 10  2006 000114420406019166 -> /usr/local/ftp/edgar/data/1000045/06/000114420406019166
lrwxrwxrwx   1 1019     bin            55 Jun 16  2006 000114420406025049 -> /usr/local/ftp/edgar/data/1000045/06/000114420406025049
lrwxrwxrwx   1 1019     bin            55 Jun 29  2006 000114420406026610 -> /usr/local/ftp/edgar/data/1000045/06/000114420406026610
lrwxrwxrwx   1 1019     bin            55 Jan 18  2007 000114420407002274 -> /usr/local/ftp/edgar/data/1000045/07/000114420407002274
lrwxrwxrwx   1 1019     bin            55 Feb  4  2009 000114420409005244 -> /usr/local/ftp/edgar/data/1000045/09/000114420409005244
problem 1:
why i can't use the command to save the output in  my  file?
ftp> dir  /edgar/data/1000045/  > /home/pt/myfile
usage: dir remote-directory local-file
problem 2:
if i want to get all the files  which is under  /edgar/data/1000045
how can i do?
any advice appriciated

---

### Post by MaindotC on 2010-09-07
Go to the directory that has all the files you want.  Then, GET all the files using the "*" wildcard.  If it is /edgar/data/1000045/ then type:
```

cd /edgar/data/1000045/
get *

```

---

### Post by bab1 on 2010-09-07
> **luofeiyu said:**
> think for your help.
i am an investor in china, want to buy some usa stock,first of all , i need some public material to value the company.
when i use command in my console:
 dir  /edgar/data/1000045/  
i can get output such as:
lrwxrwxrwx   1 1019     bin            55 Jan 25  2006 000114420406002619 -> /usr/local/ftp/edgar/data/1000045/06/000114420406002619
[COLOR="Red"]**lrwxrwxrwx**[/COLOR]   1 1019     bin            55 Feb  1  2006 000114420406003517 -> /usr/local/ftp/edgar/data/1000045/06/000114420406003517
...
problem 1:
why i can't use the command to save the output in  my  file?
ftp> dir  /edgar/data/1000045/  > /home/pt/myfile
usage: dir remote-directory local-file
Remember you are in an FTP shell.  This shell has limited commands.  You can see what is available with a "?" at the prompt.  

In addition the listing shows that these are links rather than actual files (see red above). There are no files to be uploaded from that directory.  These links may not be able to be uploaded either.  See the instructions on the web page you noted: [_http://www.sec.gov/edgar/searchedgar/ftpusers.htm_]("http://www.sec.gov/edgar/searchedgar/ftpusers.htm").> 
problem 2:
if i want to get all the files  which is under  /edgar/data/1000045
how can i do?
any advice appriciated
Use the web based EDGAR database: [http://www.sec.gov/edgar.shtml]("http://www.sec.gov/edgar.shtml").

The FTP site is really for bulk downloads.  The public data is used by such publishers as Moody's and Morningstar for their databases.
[COLOR="Navy"]**Edit**: I just ran the search on the 1000045.  This produces this list: [_http://www.sec.gov/cgi-bin/browse-edgar?company=&match=&CIK=1000045&filenum=&State=&Country=&SIC=&owner=exclude&Find=Find+Companies&action=getcompany_]("http://www.sec.gov/cgi-bin/browse-edgar?company=&match=&CIK=1000045&filenum=&State=&Country=&SIC=&owner=exclude&Find=Find+Companies&action=getcompany")  I believe this is what you want. NICHOLAS FINANCIAL INC CIK#: 0001000045[/COLOR]

---

