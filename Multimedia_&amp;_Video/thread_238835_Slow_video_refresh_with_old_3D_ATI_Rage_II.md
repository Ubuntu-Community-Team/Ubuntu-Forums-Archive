---
title: "Slow video refresh with old 3D ATI Rage II"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by dafi on 2006-08-18
Hi to all,

I have an old computer with Windows XP 512 Mb RAM and the ATI Rage II 3D graphics card.

I've installed Ubuntu and all works fine but the video refresh is very slow.
Under WinXP the refresh is very good but under Ubuntu is awful.
Coonsider that the login screen is displayed in about 1 second under WinXP is so fast that you **can't** calculate how long is the refresh time.

Where can I find better drivers compatible with my old 3D ATI Rage II?

---

### Post by Ziox on 2006-08-18
> **dafi said:**
> Hi to all,

I have an old computer with Windows XP 512 Mb RAM and the ATI Rage II 3D graphics card.

I've installed Ubuntu and all works fine but the video refresh is very slow.
Under WinXP the refresh is very good but under Ubuntu is awful.
Coonsider that the login screen is displayed in about 1 second under WinXP is so fast that you **can't** calculate how long is the refresh time.

Where can I find better drivers compatible with my old 3D ATI Rage II?

I'm assuming that you are using the ati driver that came with Ubuntu (without any driver installation or hacking).  Then I assume that you can manually change the refresh rate, just make sure that you don't damage your monitor by putting the refresh rate too high or too low.

Easy Method:

sudo dpkg-reconfigure xserver-xorg

Hard Method:

gksudo gedit /etc/X11/xorg.conf

add these two lines to your "Monitor" Section:

[B]HorizSync       28-51
        VertRefresh     43-60[/B]

Change the values to the appropriate value given in your monitor's manual.

After either method, you have to either reboot (recommended by me) or log off, and hit ctrl+alt+backspace.

---

### Post by dafi on 2006-08-18
> **Ziox said:**
> I'm assuming that you are using the ati driver that came with Ubuntu (without any driver installation or hacking).  

Yes this is a fresh installation

> **Ziox said:**
> Then I assume that you can manually change the refresh rate, just make sure that you don't damage your monitor by putting the refresh rate too high or too low.
This sounds a bit dangerous, I'm using a new LCD 19'' monitor...

> **Ziox said:**
> 
Easy Method:

sudo dpkg-reconfigure xserver-xorg

Hard Method:

gksudo gedit /etc/X11/xorg.conf

add these two lines to your "Monitor" Section:

[B]HorizSync       28-51
        VertRefresh     43-60[/B]


Is it possibile to determine the value used by Windows XP?

> 
Change the values to the appropriate value given in your monitor's manual.

BTW I can use the values reported on monitor's manual

> 
After either method, you have to either reboot (recommended by me) or log off, and hit ctrl+alt+backspace.

Sure, thanks for your hints

---

### Post by Ziox on 2006-08-18
> **dafi said:**
> Yes this is a fresh installation


This sounds a bit dangerous, I'm using a new LCD 19'' monitor...

Yeah..don't want to damage that...

> Is it possibile to determine the value used by Windows XP?

Yes, you can. I don't have windows running right now (dual boot), but i think you can find out from Control Panel => Display => Uh...Setting (I think) => Advanced...I don't remember too clearly, but just play around, and you should find it.

> BTW I can use the values reported on monitor's manual

That would be the best


> Sure, thanks for your hints

Sure :p

---

