---
title: "Need help to get video out over HDMI with Nvidia ION"
date: 2012-01-04
forum: Multimedia Software
---

### Post by niad on 2012-01-04
I have a Shuttle XS35GT (not V2) with Nvidia ION graphics and both VGA and HDMI out. Recently i installed Ubuntu 11.10 from Live CD and hooked it up to my Philips 47" LCD with the HDMI cable only. Nothing happened, no picture, the TV just said "No Signal".

I rebooted and took the cable out and in again a couple of times and suddenly i got perfect 1080p resolution and sound over HDMI (output2 i think). I used Skype and watched Youtube and was very happy. After that i have only gotten "No Signal" and whatever i do o do not get anything out on the TV. The only thing i got out of this was that It can work and very good to, but how can i recreate this every boot???

I have now tried both Ubuntu X64 and X86 and even Fedora 16 Live CD, i have updated to the latest Nvidia Driver from the Nvidia site and i have tried surely about 50 or more xorg.conf files i have found on the net that works for folks with different LCD screens. Nothing works. Sometimes i get 640x480 and sometimes i get "Signal not supported" but most often i get "No Signal".

My Philips LCD is a model 47PFL7403H
[https://docs.google.com/open?id=1F9WQ_Jb5KIvA_PbL61vC8BNXqppjRt5Z_4pp68MUq3EH82Udi1NRKHtOitHD](https://docs.google.com/open?id=1F9WQ_Jb5KIvA_PbL61vC8BNXqppjRt5Z_4pp68MUq3EH82Udi1NRKHtOitHD)

I have not been able to get any Modelines for it because it is a problem with Philips that it does not send thee EDID signal i have read. When i try different guides to get out modes supported i get nothing, Ubuntu / Nvidia does not find a device. Therefore i have just tried with random xorg.conf files i have found and hoped to get lucky sometime. I have been on this for a week now and i am about to give up if i don't get any help.

I have now Ubuntu 11.10 X64 with the latest Drivers from Nvidia installed and everything works great on my Dell U2410, i get full HD immediately when i connect over HDMI but the TV is still saying "No Signal", i am about to go crazy over this.

Please, any help is appreciated.

---

### Post by BicyclerBoy on 2012-01-04
Is the HDMI cable connected thru' an AVR HT amp  or direct ?

Can you clarify when you get "no signal" ?
Do you mean just after reboot before the X server starts up ?

There is nothing special about the HDMI modelines for your TV.

You should not need any xorg.conf file..
I would backup/delete any existing file..
You can interrogate the EDID & save to file with nvidia-settings.

If you add this to /etc/X11/xorg.conf you will get lots of debug info in /var/log/Xorg.0.log:
Option "ModeDebug"  "True"

Can you remote connect to this computer ?
The log file will reveal if the TV is not detected by X server.

---

