---
title: "How to: Watch TV with Hauppauge PVR150/250/350/500"
date: 2009-12-24
forum: Multimedia Software
---

### Post by HappyFeet on 2009-12-24
I have a Hauppauge PVR150 card running on my box, but the following tutorial will also work on the PVR250,350, and 500.

Do:
```
sudo apt-get install ivtv-utils vlc
```

Open VLC player

Media -> Open Capture Device -> PVR (from pull down menu) -> Play.

Then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

Which changes the channel. (this is for people that have cable coming into their computer directly, and NOT coming from the cable box)

If your signal is coming from a cable or satellite box, do **ivtv-tune -c3** and change the channel on the box.

```
ivtv-tune -h
```

To see the options which control the card. 


For a cool desktop tv remote,(so you dont have to use terminal to change channels, or to start tv) go to: [http://sourceforge.net/projects/tvremote/](http://sourceforge.net/projects/tvremote/)    Highly recommended. I have attached a pic of the remote below.

Remember to have Java installed first. Then you can right click>properties> open with> java. After that, just click normally to launch.

To record tv while you're watching, in VLC, go to Views and check off advanced contols. You will then see a record button in vlc's interface. All recordings will be saved to your home folder.

To schedule a tv for future viewing, we are going to use cron for the job.

We need to make sure you are a member of the crontab group first. Go to System>Administration>Users and Groups and unlock the window by clicking the keys button, or the "unlock" button. Enter password. Then click on Manage Groups button. Scroll down until you see the **crontab** entry. Highlight it, and then click on Properties. Check your name if it is not already. Log out and then back in.

First, select which channel you want to record by: (we will use channel 25 as an example)
```
ivtv-tune -c25
```
Then, in the same terminal window, do:
```
crontab -e
```
Delete everything you see in there.

Then as an example of a recording you want done on Dec. 31 4:00 PM to 5:30 PM, you would enter in crontab: (see below for an explanation of how cron works)
**# start recording**
**00 16 31 12 05 cat /dev/video0 > /home/user_name/name_of_show.mpg**
**# stop recording**
**30 17 31 12 05 killall cat**

To save the job, do **Ctrl-X** then **Y** then **Enter**.

Remember to put *your user name* in after /home. You can name the show whatever you want, just make sure you have **.mpg** after the name.

For those not familiar with cron, in the line **00 16 31 12 05 cat /dev/video0 > /home/user_name/name_of_show.mpg** 

**00** represents the minutes of the hour (4:**00**), **16** is the hour (**4**:00 a 24 hour clock is used. 12 midnight would be 00, 1 AM would be 01, etc.), **31** is the date, **12** is the month, **05** is the day of the week -Thurs. in this case. (Sunday is 00, Monday is 01, etc)

You may also find the following link useful. Thanks to MeKino for this. [http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

### Post by sjk44 on 2009-12-25
HappyFeet - 

Thank you so much for the tutorial, it is exactly what I have been looking for!!  I also am located in Connecticut.  I am running Ubuntu 9.10 on a Shuttle system with a 4-core AMD processor.  Where can I get the best Hauppauge adapter to accept a signal directly from my cable system (without a cable box)?  Which Hauppauge adapter would be best?  Can I use a USB Hauppauge connector (which I would prefer)?

Thank you - again.

---

### Post by HappyFeet on 2009-12-25
Ebay would probably be the best place to pick up a Hauppauge PVR150 pci card since they are hard to find. My tutorial is specifically for PCI cards, and I doubt the usb version would work with what I wrote.

Edit: [Here]("http://cgi.ebay.com/HAUPPAUGE-HP-WINTV-PVR-150-MCE-PCI-NON-5187-8395_W0QQitemZ400093138964QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item5d2768d014") is one for sale on Ebay for $34. Pretty good deal, considering I paid $80 a few years ago.

Where in CT are you? I'm in Stratford.

---

### Post by sjk44 on 2009-12-26
HappyFeet - thank you!!  

I bought the card and will install it as soon as it arrives.  I apologize for being tardy in this response, but I am now in Ireland for the holidays.  Normally we live just down the 'pike from you in Stamford.

Best wishes for a happy and healthy New Year!  Thank you again.

---

### Post by saedelaere on 2009-12-27
I'am writing a frontend to watch and record TV for ivtv, pvrusb2 and cx18 devices. Perhaps you might find it useful too. See this [thread]("http://ubuntuforums.org/showthread.php?t=763698&page=14") for details.

Regards

---

