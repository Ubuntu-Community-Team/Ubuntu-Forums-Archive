---
title: "How to store recordings on external hdd?"
date: 2013-08-18
forum: Multimedia Software
---

### Post by andy_uk2 on 2013-08-18
Hi all, 

I'm a beginner with Ubuntu so I hope I can explain this correctly. I want to record a week's worth of atmospheric sound using arecord. I have a 2 TB external hard drive where I want to store the recordings. I've installed Ubuntu 12.10 on my Windows 7 computer and mounted the external hdd successfully. For taking the recordings I'm using a script that uses the arecord function. However, even after copying the script onto the external hdd and running it from there, I can't get it to store data in the ext hdd itself. All the recordings get stored in the home folder instead. How can I store the recordings on the ext hdd? Is there a path I need to specify on the script? Or do I need to install Ubuntu on the ext hdd itself? 

Any help will be greatly appreciated.

---

### Post by evilsoup on 2013-08-18
Could you maybe paste your script here? Put it in between [code ][ /code] tags.

---

### Post by agillator on 2013-08-18
I know nothing of the specific program you are using, but would be very surprised if you did not have control over the output file(s). First, see if there is a man page for your program (not the script) and if there is see what it says. Assuming there is an option for the output, then check the script and see how the program is called in there. I am assuming the script is actually a text file (bash, perl, python or something). You may not know the particular language but you should be able to understand what it is doing. Then a change to the script . . . .

Another choice is to move the files yourself either by script or manually. It would not be difficult to write a script in bash that calls the script you are using and, when it is finished, moves the files. Another option would be a simple cron command to move the files once a day or once an hour or whatever. For example, an entry in cron (using crontab -e ) sud as 15 */4 * * *  mv /<file locations>/<file names> /<external drive> would do it every four hours at 15 minutes after the hour. See man crontab for instructions. the <. . . .> are just placeholders for the actual info, of course.

---

