---
title: "Installing drivers for Nvidia 8500GT"
date: 2011-01-23
forum: Multimedia Software
---

### Post by Chris Psycho on 2011-01-23
Ok, I'm having another go at ubuntu!

I have Ubuntu 10.10 running (a fresh install).

I went to the nvidia site and downloaded the linux drivers for it, (it's a .run file).

So I try runnig it via the terminal, it goes great untill it mentions that I need to exit the X Window system?

So I tried pressing ctrl+alt+f2 (switches to a root terminal?) and tried runnig it from there but no luck either...

Can anyone advise me on how to do this? Thank you!

---

### Post by themusicalduck on 2011-01-23
Rather than download it from the Nvidia site, go to System > Administration > Additional Drivers and see if you can install it from there.

---

### Post by Chris Psycho on 2011-01-23
I'll try that now. A quick question, how do you dial up with ubuntu?

---

### Post by Chris Psycho on 2011-01-23
I found it! Now it seems I just need the right APN(with the internet dongle).

Anyway when I click on 'additional drivers' i get a error 'Downloading packages indexes failed, please check your network status. Most drivers will not be available.'

I'm not connected to the internet. What should I do next?

---

### Post by themusicalduck on 2011-01-23
Have a look through [http://www.google.co.uk/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=ubuntu+dial+up](http://www.google.co.uk/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=ubuntu+dial+up) one of those pages should help.

---

### Post by themusicalduck on 2011-01-23
> **Chris Psycho said:**
> I found it! Now it seems I just need the right APN(with the internet dongle).

Anyway when I click on 'additional drivers' i get a error 'Downloading packages indexes failed, please check your network status. Most drivers will not be available.'

I'm not connected to the internet. What should I do next?

You need to be connected to download the driver through that.

If you do want try installing it manually instead, try pressing ctrl+alt+f1 again, then run this command (any open programs will be closed) ```
sudo service gdm stop
```  then try running the .run file again.

---

### Post by Chris Psycho on 2011-01-23
Haha thanks man! Off I go(to restart my pc and boot to ubuntu)!

What does that command do if I may ask?

---

### Post by themusicalduck on 2011-01-23
No problem!

It closes down Gnome the display manager for Ubuntu and so closes down X at the same time (which is what the error was complaining about).

---

### Post by Chris Psycho on 2011-01-23
Yay it worked.. The second time round though?

At first it gave a load of error messages and stated it's gonna write a file to disable something?

Anyway the second time I ran it went like this:

The distribution provided pre-install script failed. Contine installation anyway?

Yes

Would you like to run the nvidia xconfig utillity to automatically update your xconfig file so that the nvidia x driver will be used when you restart x? Any pre-existing xconfig file will be backed up.

Yes

Now it boots up fine, but my screen resolution seems to only have two options, 640x480 and 320x240. 

If I go to moniter setup(I think) it says something that I can only used the nvidia provided configuration or something?

Within the nvidia 'contol panel/?' it only gives two screen resolutions.

Thank you for your help so far.

---

### Post by Skeletech on 2011-11-04
I'm havin the same problem with a fresh install of Ubuntu 11.10..cant seem to find the right drivers for my 8500GT or proper way to install it

---

### Post by Skeletech on 2011-11-18
did ya get the nvidia problem fixed? I'm having the same problem...updated drivers and only get half the resolution I did before..now I cant get the old drivers back

---

