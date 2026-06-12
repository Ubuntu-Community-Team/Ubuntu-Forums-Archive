---
title: "My Gigabyte ATI RADEON X800 XL Stutters"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by Straider&#1613; on 2007-12-11
I've  Installed      Ubuntu 7.10    a week ago and it's totally awesome 
But when I tried to install my driver with restricted manger  because it popped to me at startup

So when I install it by the manger
BUT i went to the Screensavers to test it

I found that it's sooooooo Ugly whith many flickers and sometime the computer just freeze and i have to Restart it :mad:

And when I Install CompizFusion it has the same problem the Screensavers
The effects has many flickers in it and sometimes i have a freeze :(
And for a week i searchd the net for somethin but No Hope for me

My Driver is Gigabyte ATi Radeon  X800 Xl

Help is appreciated

Thank You

---

### Post by kubug on 2007-12-11
You may have some driver issues. A quick way to see if you do is to download and install "Envy".

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Current Version is 0.9.9-ubuntu2, which you can find here: 
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb")

Download it and double click it. Click on install and enter password. Then go to "Applications->System Tools->Envy"

Select the Ati Driver install. It will do everything for you. It will ask to change your xorg.conf (click Yes) and then reboot.

This will have installed the latest drivers. 

In case you need to undo the xorg.conf change, it created a backup file in /etc/X11/xorg.conf.back_<todaysdate>. 

Hope this helped.

---

