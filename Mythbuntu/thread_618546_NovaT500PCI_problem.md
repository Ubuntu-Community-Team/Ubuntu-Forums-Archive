---
title: "NovaT500PCI problem"
date: 2007-11-20
forum: Mythbuntu
---

### Post by Al_Vampyre on 2007-11-20
Think this is probably a power saving problem but thought I'd ask for some advice. I have a Novat500 PCI that until this Mythbuntu distro I really struggled with. It's all working now apart from one small thing.

If the HTPC has been on for a long time, like while I'm out at work, when I switch on it doesn't seem to tune in, all I get is a partial lock. This of course means that if I have a recording scheduled it doesn't record. My workaround is to reboot the machine when I come home each night and then everything works.

Problem is I'm going away this weekend and know that the scheduled recordings I have planned for Friday will work but the rest will probably fail. Anyone heard or know of a possible solution?

The only thing I have thought of so far is a reboot script that runs every 12 hours or so just to keep the tuners alive long enough, the only issue with that is that it may cause a rebbot during a scheduled recording.

If anyone has any ideas I'd be glad to hear them

Thanks in advance

---

### Post by davecurtains on 2007-11-20
I had some problems with my Nova-T500 at the start - mainly it not being recognised.

I followed the guide here and now it works great:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_)

You may have already tried that - but it worked for me on 7.10 Ubuntu.

---

### Post by Al_Vampyre on 2007-11-21
Thanks for that, as I said the card works just fine, apart from the fact that I think the USB tuners are going to sleep after a period of inactivity and do not wake properly. It takes a reboot to kick them back into action.

---

### Post by roseway on 2007-11-21
There's a known problem with the Nova-T 500 whereby it loses the TV signal from time to time, and the only solution is to reboot. I got bitten by the same bug and changed to a different TV card. According to linuxtv.org this should be fixed now (see [http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage](http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage) ) but I don't think it is.

---

### Post by Nikas on 2007-11-21
> **roseway said:**
> There's a known problem with the Nova-T 500 whereby it loses the TV signal from time to time, and the only solution is to reboot. I got bitten by the same bug and changed to a different TV card. According to linuxtv.org this should be fixed now (see [http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage](http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage) ) but I don't think it is.

I have 2 Nova-T 500 in my server.
Works great! I got some problems (I2C write error) when i had the ir-remote-cable connected. No problems without it. :) In my case i dont need to have the ir-cable connected..
Installed the latests v4l-dvb-drivers and firmware too.

---

### Post by roseway on 2007-11-22
> **Nikas said:**
> Installed the latests v4l-dvb-drivers

Ah yes, that may well be the solution.

---

### Post by Lem on 2007-11-22
I had the same. Updated the firmware and drivers and it seemed to fix it. Updated the drivers again and it started playing up.

Now now done another update.. fingers crossed!

---

### Post by Al_Vampyre on 2007-11-22
Thanks for your input guys, I am using the latest firmware (I think!), maybe I'll try reinstalling and see if it helps.

---

### Post by sygin on 2008-01-05
Hi,

My Hauppauge Nova-T 500 USB disconnect/dropout issues are not completely solved.

I have a MythTV box with:
MythTV 0.20.2
Hauppauge Nova-T 500 DVB-T PCI card
I am using firmware dvb-usb-dib0700-1.10.fw
Latest linux.tv source compile
on a Ubuntu 7.10 install.

The disconnect problems are very much better than they were using dvb-usb-dib0700-03-pre1.fw

The problem is that I occasionally get a 'dmesg' error:
mt2060 I2C read failed

After this error I lose the ability to get a picture when using one of the DVB-T tuners. Usually only one tuner is affected, the other still works fine. A MythTV Backend restart fixes this problem but it is annoying.

Does anyone else have this problem?

Thank You,
Sygin

PS: As a temporary work around, I am using a very simple program that will restart MythTV if there is a mt2060 error. If you are interested in this application reply to this thread.

---

### Post by Nikas on 2008-01-05
> **sygin said:**
> Hi,

My Hauppauge Nova-T 500 USB disconnect/dropout issues are not completely solved.

I have a MythTV box with:
MythTV 0.20.2
Hauppauge Nova-T 500 DVB-T PCI card
I am using firmware dvb-usb-dib0700-1.10.fw
Latest linux.tv source compile
on a Ubuntu 7.10 install.

The disconnect problems are very much better than they were using dvb-usb-dib0700-03-pre1.fw

The problem is that I occasionally get a 'dmesg' error:
mt2060 I2C read failed

After this error I lose the ability to get a picture when using one of the DVB-T tuners. Usually only one tuner is affected, the other still works fine. A MythTV Backend restart fixes this problem but it is annoying.

Does anyone else have this problem?

Thank You,
Sygin

PS: As a temporary work around, I have written a very simple program that will restart MythTV if there is a mt2060 error. If you are interested in this application reply to this thread.

Do you have the ir-cable connected to your card?
If so, try whithout it.

I would like to see your script. :)

---

### Post by sygin on 2008-01-05
Hi,

I have my remote connected, but find that it is very useful and using mythwatch am satisfied with the results.

I have attached mythwatch the application that restarts the MythTV backend when it detects a mt2060 error. It is tested on Ubuntu 7.10.

See the README and INSTALL files for details.

Cheers
Sygin

---

### Post by Lem on 2008-01-06
I've installed your script Sygin. Will see how it goes!

---

### Post by boy lex on 2008-01-22
Thanks for the script.
Have installed it. Will report back if it's not working.
Running 7.10

---

### Post by boy lex on 2008-01-25
Seems to be working great. Except that I got home this arvo and found that the backend was down after a mt2060 I2C read failed. I think that the restart failed.

Would it be better to get the script to stop it completely then wait 30 secs and start it. Obviously you lose 30 secs of a show if you're in the middle of a recording!

Thanks for the script!

---

### Post by sygin on 2008-01-29
Hi,

If you look in the log file, it will let you know what has been going on.

i.e.

bob@media:~$ cat /var/log/mythwatch.log
[27-1-08 17:02:21] --- Started ---
[27-1-08 19:51:02] --- Started ---
[27-1-08 23:50:20] --- Started ---
[29-1-08 05:41:07] ERROR: Disconnect Detected.
[29-1-08 05:41:07] ACTION: Attempting mythtv-backend restart.
[29-1-08 19:36:37] ERROR: Disconnect Detected.
[29-1-08 19:36:37] ACTION: Attempting mythtv-backend restart.
bob@media:~$


ERROR: Disconnect Detected.  - this happens when there is a mt2060 error

 ACTION: Attempting mythtv-backend restart - This executes the command: /etc/init.d/mythtv-backend restart

If you encounter a problem it would be useful to have a copy of the relevant part of the "dmesg" output and a copy of the mythwatch.log file.

I am thinking about releasing a newer version that will list the output of mythtv-backend restart. This will help to check for restart issues.

Thanks,
Sygin

---

### Post by boy lex on 2008-02-02
Thanks Sygin

I've been monitoring the log file along with dmesg. I've now got two of these cards running in my box... Yes 4 tuners!

It seems that on occasion a tuner will lock up without any entry in the dmesg. Has anyone else experienced this.

I was also having problems with the backend just disappearing, so I wrote a really simple script as a cronjob to check if it's running, start it if it's not and add a log to a file if it's not.

Looking around further on this problem, it appears that the problem is somehow related to mythbackend using the EIT data. Since I use radiotimes xmltv for my listings and only had EIT switched on for radio, I decided to turn it off. All the tuners have been rock solid for a couple of days now and no errors in the dmesg either.

Hopefully there'll be a fix for the firmware/drivers on the v4l-dvb soon enough.

I'll let you know if the EIT solution actually stays working.

---

### Post by Nikas on 2008-02-02
I have 2 cards in my server too.
Had problems with EIT enabled. The backend just crashed after leaving a message about EIT-scanning in the logs.
Had some i2c-read-errors when i had the remote cable connected to the cards.

Now i dont use EIT (just xmltv) or remote cable and i have no problems with tuning or disconnects.

---

