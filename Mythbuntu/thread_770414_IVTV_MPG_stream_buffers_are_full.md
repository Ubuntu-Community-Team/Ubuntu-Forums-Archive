---
title: "IVTV MPG stream buffers are full"
date: 2008-04-27
forum: Mythbuntu
---

### Post by Chuckels550 on 2008-04-27
I upgraded from a fully functional Mythbuntu 7.10 to 8.04 and now I cannot display live TV nor can I display any TV recordings. The xfce desktop and the mythtv interface are working and displaying.  When I try to use the live tv or display a tv recording the screen goes black and hangs until I ctl+alt+backspace and start another session. When I check dmesg, I see the following error.

ivtv0: All encoder MPG stream buffers are full. Dropping data.
ivtv0: Cause: the application is not reading fast enough.

Is this a problem with the IVTV drivers and how do I fix it?

Strangely enough I can see the thumbnail videos for the recorded programs, but just cannot play the recordings.

AMD Athlon 64 3500+, 2GB RAM
MSI K8N Neo2 Platinum (MS-7025) Socket 939 Mobo
Hauppauge WinPVR 350
Hauppauge WinPVR 150
Asus Nvidia N7600GS Graphics Card
Creative Labs Soundblaster Audigy X-Gamer

---

### Post by ian dobson on 2008-04-27
Hi,

Try creating a new file /etc/modprobe.d/ivtv.conf and add the text:-
options ivtv enc_mpg_buffers=8

Then reboot the system to reload all the drivers.
Maybe that might help (It just adds extra buffers for IVTV).

Regards
Ian Dobson

---

### Post by Chuckels550 on 2008-04-27
> **ian dobson said:**
> Hi,

Try creating a new file /etc/modprobe.d/ivtv.conf and add the text:-
options ivtv enc_mpg_buffers=8

Then reboot the system to reload all the drivers.
Maybe that might help (It just adds extra buffers for IVTV).

Regards
Ian Dobson

There is no exiting /etc/modprobe.d/ivtv.conf file.  Should there be or is this either an error or an undocumented change in Hardy Heron?

---

### Post by ian dobson on 2008-04-27
Hi,

In the good old days/on some linux systems there is a modules.conf file. Ubuntu uses the modules.d directory for parameters/options for modules.

As the change is for the ivtv module I though the name ivtv.conf is  good name for the file.

just do the following as root/su
sudo nano /etc/modprobe.d/ivtv.conf

add the line
options ivtv enc_mpg_buffers=8

the control x, to save the file.

Regards
Ian Dobson

---

### Post by Chuckels550 on 2008-04-28
> **ian dobson said:**
> Hi,

In the good old days/on some linux systems there is a modules.conf file. Ubuntu uses the modules.d directory for parameters/options for modules.

As the change is for the ivtv module I though the name ivtv.conf is  good name for the file.

just do the following as root/su
sudo nano /etc/modprobe.d/ivtv.conf

add the line
options ivtv enc_mpg_buffers=8

the control x, to save the file.

Regards
Ian Dobson

Thanks, your solution fixed the error message problem, but I still cannot get any TV playback.  I think that the TV Playback is also configured badly for my system.  What should it be with a TV Playback using my set-up and displaying on an Sharp Aquos LCD TV at 1080i? 

I also seem to have problems with the Mythbuntu Control Center - the Optimize MYSQL Tables button doesn't do anything.  Before when I used the button, it would open a terminal window and run the script and then close the window, now it just flickers when I click the button.

---

### Post by ian dobson on 2008-04-29
Hi,

What graphic card are you using/what driver are you using.

I hope it's a nvidia :)

For best results you should use the proparitery driver rather than the generic/open source one.

When you try TV playback what do you see? Are there any error messages in your mythtv log file? The log files are usually in /var/log/mythtv.

Regards
Ian Dobson

---

### Post by Chuckels550 on 2008-04-29
Problem solved - I ran the optimize mysql script first, then set the TV Playback setting CPU++ to match the 1080i setting I have been enjoying and it worked.  I now have better TV playback resolution in Hardy Heron (1080i) than I had with Gutsy Gibbon (720p).

Thanks Ian

---

