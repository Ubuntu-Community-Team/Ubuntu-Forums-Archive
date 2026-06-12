---
title: "installing WinTv pvr-250 ubuntu 9.10"
date: 2010-02-07
forum: Multimedia Software
---

### Post by Bomaz on 2010-02-07
How do I install WinTv pvr-250 (Tv-card) on my ubuntu 9.10 Karmic Koala?

I am new to linux and not quite sure to begin. I would like to be able to use it to watch TV on my computer, using VLC, mythTV or similar.

Anyone know how to go about accomplishing this?

---

### Post by BubbaBlues on 2010-03-08
I have the same hauppauge card. Looks like we're just S.O.L.

---

### Post by Bomaz on 2010-03-11
solved, the keyword is TV-Viewer, that works

---

### Post by J_Stanton on 2010-03-11
found this in the archives.  I have a Hauppauge PVR150 card running on my box, but the following tutorial will also work on the PVR250,350, and 500.  Do: ```
sudo apt-get install ivtv-utils vlc
```  Open VLC player  Media -> Open Capture Device -> PVR (from pull down menu) -> Play.  Then you can do (in terminal)  ```
ivtv-tune -c25
``` (25 is channel number)  Which changes the channel. (this is for people that have cable coming into their computer directly, and NOT coming from the cable box)  If your signal is coming from a cable or satellite box, do **ivtv-tune -c3** and change the channel on the box.  ```
ivtv-tune -h
```  To see the options which control the card.    For a cool desktop tv remote,(so you dont have to use terminal to change channels, or to start tv) go to: [http://sourceforge.net/projects/tvremote/](http://sourceforge.net/projects/tvremote/)    Highly recommended.  Remember to have Java installed first. Then you can right click>properties> open with> java. After that, just click normally to launch.  To record tv while you're watching, in VLC, go to Views and check off advanced contols. You will then see a record button in vlc's interface. All recordings will be saved to your home folder.  To schedule a tv for future viewing, we are going to use cron for the job.  We need to make sure you are a member of the crontab group first. Go to System>Administration>Users and Groups and unlock the window by clicking the keys button, or the &quot;unlock&quot; button. Enter password. Then click on Manage Groups button. Scroll down until you see the **crontab** entry. Highlight it, and then click on Properties. Check your name if it is not already. Log out and then back in.  First, select which channel you want to record by: (we will use channel 25 as an example) ```
ivtv-tune -c25
``` Then, in the same terminal window, do: ```
crontab -e
``` Delete everything you see in there.  Then as an example of a recording you want done on Dec. 31 4:00 PM to 5:30 PM, you would enter in crontab: (see below for an explanation of how cron works) **# start recording** **00 16 31 12 05 cat /dev/video0 > /home/user_name/name_of_show.mpg** **# stop recording** **30 17 31 12 05 killall cat**  To save the job, do **Ctrl-X** then **Y** then **Enter**.  Remember to put *your user name* in after /home. You can name the show whatever you want, just make sure you have **.mpg** after the name.  For those not familiar with cron, in the line **00 16 31 12 05 cat /dev/video0 > /home/user_name/name_of_show.mpg**   **00** represents the minutes of the hour (4:**00**), **16** is the hour (**4**:00 a 24 hour clock is used. 12 midnight would be 00, 1 AM would be 01, etc.), **31** is the date, **12** is the month, **05** is the day of the week -Thurs. in this case. (Sunday is 00, Monday is 01, etc)  You may also find the following link useful. Thanks to MeKino for this. [http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

