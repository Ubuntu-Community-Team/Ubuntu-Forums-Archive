---
title: "cron help needed"
date: 2008-08-07
forum: Mythbuntu
---

### Post by petermichael on 2008-08-07
Updated:
I found that fcron works fine with the same script and settings...

Hi all

I try to run a ripper-script using cron in order to populate the myth tv-guide.
But it does not work. 
I have tried "everything".

This script runs ok:
#!/bin/sh
echo "test" > /home/peter/test.txt

This script does not run ok:
#!/bin/sh
cd /home/peter
nice python /home/peter/xmltv/tv_grab_dk_all.py --out ud.xml
nice /usr/bin/mythfilldatabase --update --file 1 ud.xml

I cannot find anything in the log messages. 
Any ideas for further trace? 
What is not correct in script number two?
Please note that it runs perfectly from the command line.

I use this version of cron: 3.0pl1-100ubuntu2

All help is very welcome
Thanks
Peter

---

