---
title: "bad audio in cropped wmv; avidemux"
date: 2009-10-19
forum: Multimedia Software
---

### Post by chitowner2 on 2009-10-19
I have a file identified as asf video, which I understand is essentially a container format for wmv/wma. The file I have is in 4x3 format with black bars above and below, so I am trying to crop it back to it's original ratio with Avidemux. 

I have tried a variety of video and audio formats, but the resulting file always has bad audio, either all pops and crackles, or far out of sync. Compared to the original for example, approx 15 sec of audio gets dropped off the beginning when I am saving with MPEG4/AVC + AAC audio.

Can any Avidemux wizard tell me what's wrong and/or how to get this right?

Thanks!
:)

---

### Post by vinutux on 2009-10-19
Try **[handbrake]("http://handbrake.fr/")** it auto cropping i think....

---

### Post by chitowner2 on 2009-10-22
Hmmm... installing Handbrake isn't trivial. Apparently it's not available with apt-get or synaptic. I had to download a .deb file for ver 0.9.3. There is some buzz about problems with 0.9.4 on koala, so I decided the previous stable ver would be a better option.

I'll try to report back on results.
CT

---

### Post by chitowner2 on 2009-10-22
OK, installed the deb file and have a kmenu item for Handbrake under multimedia, but when I try to open that I get an error: 

"Unable to create ghb. Could not parse UI description"

SO that's a wall for me because I have no idea what that means. 

Help?
:confused:
CT

---

### Post by vinutux on 2009-10-22
open it in terminal ```
ghb
```

post the output here................

---

### Post by chitowner2 on 2009-10-22
> **vinutux said:**
> open it in terminal ```
ghb
```

post the output here................


Here it is:

$ ghb

(ghb:5461): Gtk-WARNING **: Failed to set property GtkToolbar.icon-size to GTK_ICON_SIZE_DND: Could not parse integer `GTK_ICON_SIZE_DND'


Hope that tells *you* something vinutux!
CT
:P

---

### Post by vinutux on 2009-10-23
I think you are missing some gtk libraries.....

OK........ you installed it from official site....


Un install it and install from [getdeb.net]("http://www.getdeb.net/app/HandBrake") version [http://www.getdeb.net/app/HandBrake]("http://www.getdeb.net/app/HandBrake")

---

### Post by chitowner2 on 2009-10-23
Nope. Same error with that version too.  So far I have tried:
HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
handbrake-gtk_0.9.3-0getdeb1_amd64.deb
HandBrake-svn2845-Ubuntu_GUI_x86_64.deb

All of them fail to run on karmic beta/kde4.3.

Maybe I should just wait a few weeks for things to stabilize in repo-land? A friend suggested that things are in such a state of flux right now that it may not be possible to get Handbrake to run on karmic until after the stable release.

CT
:(

---

### Post by vinutux on 2009-10-23
> **chitowner2 said:**
> Nope. Same error with that version too.  So far I have tried:
HandBrake-0.9.3-Ubuntu_GUI_amd64.deb
handbrake-gtk_0.9.3-0getdeb1_amd64.deb
HandBrake-svn2845-Ubuntu_GUI_x86_64.deb

All of them fail to run on karmic beta/kde4.3.

Maybe I should just wait a few weeks for things to stabilize in repo-land? A friend suggested that things are in such a state of flux right now that it may not be possible to get Handbrake to run on karmic until after the stable release.

CT
:(

All that builds for Jaunty and below not for karmic............

This is from Handbrake ubuntu ppa for karmic try this [https://launchpad.net/~handbrake-ubuntu/+archive/ppa/+build/1199987/+files/handbrake-gtk_0.9.3+repack1-0ubuntu0~9.10jdong1_amd64.deb]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa/+build/1199987/+files/handbrake-gtk_0.9.3+repack1-0ubuntu0~9.10jdong1_amd64.deb")


Here is handbrake ppa : [https://launchpad.net/~handbrake-ubuntu/+archive/ppa ]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")

---

### Post by jms-ubuntu-en on 2009-10-28
> **vinutux said:**
> 
Here is handbrake ppa : [https://launchpad.net/~handbrake-ubuntu/+archive/ppa ]("https://launchpad.net/%7Ehandbrake-ubuntu/+archive/ppa")
Same problem with PPA's handbrake & karmic (32bit)...

---

### Post by vinutux on 2009-10-28
Dont know What that prob.... coz of i am not in karmic yet.....

And you can install cli version [very simple and powefull too]

**[http://handbrake.fr/downloads.php]("http://handbrake.fr/downloads.php")**

Here is cli help : **[http://trac.handbrake.fr/wiki/CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")**

---

### Post by Makurosu on 2009-10-28
I'm getting it too with Karmic 32-bit RC.  I installed from the Launchpad PPA.

---

