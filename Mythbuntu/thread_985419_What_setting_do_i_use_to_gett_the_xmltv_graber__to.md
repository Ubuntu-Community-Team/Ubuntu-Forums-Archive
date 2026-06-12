---
title: "What setting do i use to gett the xmltv graber  to  work for uk"
date: 2008-11-17
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-17
Hello I have 2 questions in myth 8.04 1: I am having problems with getting the write channel names displayed, instead i get numbers ie currently no:31 is C4 and so on 
my current setting are as follows GENERAL SETTINGS: TV FORMAT: PAL: CHANNEL FREQUENCY 
TABLE: europe west, I have selected xmltv as grabber VIDEO SOURCE:listing grabber United Kingdom {bleb.org} xmltv in mythbackend.I then get this message Myth tv was unable to retrieve channel information for your provider, Please check the terminal window for more information. 2nd box appears you must run mythfilldatabase -- manual the first time, instead of just mythfilldatabase. Your grabber does not provide channel numbers, so you have to set them manually.    
2: I would like to output to my analogue tv via my tv cards avi connectors is this possible if so what setting should i select.

---

### Post by SiHa on 2008-11-18
1: I found the Radio Times grabber worked, and the bleb one didn't for me. Even easier is to just use EIT data, you only get 8 days, but that's enough for me.

---

### Post by zf3636 on 2008-11-18
Hello i will try EIT data thanks

---

### Post by zf3636 on 2008-11-18
Hi i have tried EIT data, i still get numbers instead of channel names i am using a pal Wintv 150 pvr as my tv card video source, the uk ireland radio times grabber freezes at 50% channel frequincy should it be set to europe west or just left at default any ideas.

---

### Post by SiHa on 2008-11-19
> **zf3636 said:**
> Hi i have tried EIT data, i still get numbers instead of channel names i am using a pal Wintv 150 pvr as my tv card video source, the uk ireland radio times grabber freezes at 50% channel frequincy should it be set to europe west or just left at default any ideas.

I think you need to delete the input, and start again, specifying EIT only, and scanning for channels again. Then just run Mythfilldatabase after quitting the backend setup (you should be prompted to do so anyway). I'm fairly certain that's all I did. It's a few months ago now.

Also, I don't know if this thread will help:
[http://ubuntuforums.org/showthread.php?t=914136](http://ubuntuforums.org/showthread.php?t=914136)
It concerns the channel numbering in the UK.

---

### Post by zf3636 on 2008-11-19
> **SiHa said:**
> I think you need to delete the input, and start again, specifying EIT only, and scanning for channels again. Then just run Mythfilldatabase after quitting the backend setup (you should be prompted to do so anyway). I'm fairly certain that's all I did. It's a few months ago now.

Also, I don't know if this thread will help:
[http://ubuntuforums.org/showthread.php?t=914136](http://ubuntuforums.org/showthread.php?t=914136)
It concerns the channel numbering in the UK.

Thanks will try today

---

