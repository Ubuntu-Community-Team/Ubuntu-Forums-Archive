---
title: "Geforce 6600 LE"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by gbarron on 2007-02-20
Hi,

I am running ubuntu 6.10 on an AMD64 with a Geforce 6600LE graphics card.

I have installed the NVidia drivers, but I am having resolution problems.  When I start the system the login screen appears to be in a reasonable resoluton, but when I login the system places me in 640x480 and will not allow me to change it to a higher one.

I have been through several "fix" articles, but have not managed to resolve the issues.  When I go to the system menu -> "NVIDIA X Server Settings" it correctly identifies everything about my card.  I have opened xorg.conf and there are several resolutions listed against the card.  

Any help woulg be greatly appreciated.
Regards
Gary

I would like to point out that I have looked at the graphics card posts for the 6600LE found at [http://ubuntuforums.org/showthread.php?t=361240](http://ubuntuforums.org/showthread.php?t=361240), but this did not resolve my issue.  Thanks.

---

### Post by r4ik on 2007-02-20
Have not read it all but did you try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by gbarron on 2007-02-20
Hi r4ik,

Thanks for the post.  I ran the script a little while ago and it didn't fix it I'm afraid.

Regards
Gary

---

### Post by tseliot on 2007-02-20
Install the latest driver via Envy.

Then type:
```
sudo nvidia-settings
```

and set the resolution from there. Then click on "apply" and save your settings

---

### Post by r4ik on 2007-02-20
> **tseliot said:**
> Install the latest driver via Envy.

Then type:
```
sudo nvidia-settings
```

and set the resolution from there. Then click on "apply" and save your settings

Is this a overall solution ?
Stupid question forget it.

---

### Post by gbarron on 2007-02-24
> **tseliot said:**
> Install the latest driver via Envy.

Then type:
```
sudo nvidia-settings
```

and set the resolution from there. Then click on "apply" and save your settings

Hi, 

I have installed version envy_0.8.2-0unbuntu1_all.deb and ran that script from the terminal.  I then ran nvidia-settings, when this opens it shows my display as 640x480 and doesn't provide me any option to reset or override that resolution.

Any ideas?
Regards
Gary

---

### Post by tseliot on 2007-02-24
> **gbarron said:**
> Hi, 

I have installed version envy_0.8.2-0unbuntu1_all.deb and ran that script from the terminal.  I then ran nvidia-settings, when this opens it shows my display as 640x480 and doesn't provide me any option to reset or override that resolution.

Any ideas?
Regards
Gary

Try point 5 of the Problems Section of my guide:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)

---

### Post by gbarron on 2007-02-24
Hi Guys,

This problem has been resolved by the strangest of means and so I wanted to post my experience just in case anyone is suffering as I was.

I ran the scripts and the attempted to change the resolutions as directed, but to no avail.  Out of desperation I changed my monitor and then I restarted the system.  Once I did this all of the resolutions appeared as required.  I was lucky enough to have several flat panel monitors around to try this.  

I would suggest that the problem was not the drivers for the Nvidia card, but the detection of available screen resolutions from the monitor.

Thanks to everyone for the help I received, it made me more determined to persist with ubuntu.

Regards
Gary

---

