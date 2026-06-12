---
title: "playback overscan problem after 0.21 update"
date: 2008-03-26
forum: Mythbuntu
---

### Post by billionmonkeys on 2008-03-26
I'm on mythbuntu 7.10 and I pulled down the 0.21 update and since I have been having overscan issues on playback.

The main gui still fills the entire screen, but as soon as i play back a video there are these two black bars on the left and right side of the video for some reason.  I have no problem with overscan in the regular gui, but during playback these things show up.  arrgh!  any idea what settings I have to change to make them go away?  I've tried fiddling with various playback settings (horizontal scaling, different playback profiles) but they don't seem to affect the black bars that show up on the left and right.  livetv has the same problem.

my tv out device is an nvidia 7100gs with overscan set to 0.8 in xorg.conf
using svideo output.


suggestions as to what to look at would be appreciated.

---

### Post by jbman on 2008-03-27
i have the problem where its getting too big. the gui is fine, the frontend is fine but playing a file via the internal player its too big on the sides so its cutting off the edges left and right.

---

### Post by freymann on 2008-03-27
> **billionmonkeys said:**
> I'm on mythbuntu 7.10 and I pulled down the 0.21 update and since I have been having overscan issues on playback.

my tv out device is an nvidia 7100gs with overscan set to 0.8 in xorg.conf
using svideo output.


 You can go to a terminal and type:

```

nvidia-settings

```

(not sure if you need to prefix that with sudo)

Or go into the Mythtv Control Center, proprietary drivers, nvidia settings.

Adjust the overscan setting in there. It shows you the result in real time. Very handy!

---

### Post by majoridiot on 2008-03-27
> **freymann said:**
> You can go to a terminal and type:

```

nvidia-settings

```

(not sure if you need to prefix that with sudo)

Or go into the Mythtv Control Center, proprietary drivers, nvidia settings.

Adjust the overscan setting in there. It shows you the result in real time. Very handy!

this is true only for some nvidia chipsets.  unfortunately, not all chipsets have overscan support yet.

if overscan adjustment isn't available in nvidia-settings, there are also settings in frontend setup, 
under playback.  try tweaking those.  adjusting them fixes over/underscan issues with my tuners.

---

### Post by tgm4883 on 2008-03-27
Have you tried using the screen setup wizard in .21?

---

### Post by KillerKiwi on 2008-03-27
I use the nvtv tool to bump up the overscan

```
nvtv -t -s Large
```

or 

```
nvtv -t -s Huge
```

the nivida settings dosnt have overscan but nvtv still works

---

### Post by jbman on 2008-03-27
> **tgm4883 said:**
> Have you tried using the screen setup wizard in .21?

Where is that?

---

### Post by tgm4883 on 2008-03-29
> **jbman said:**
> Where is that?

It's in the frontend under setup.

---

### Post by jbman on 2008-03-30
yeh in setup now where?

---

### Post by laga on 2008-03-30
Oops. Yeah, you don't see it because mythbuntu-control-centre comes with an old version of the menu file.

I guess if you do:

```

cd /usr/share/mythtv
sudo cp main_settings.xml main_settings.xml.mcc
sudo cp main_settings.xml.diverted main_settings.xml
[code]

you can see the "screen setup wizard" menu item.

After you've done your changes, you should revert to the old xml file:

[code]
sudo cp main_settings.xml.mcc main_settings.xml

```

---

### Post by billionmonkeys on 2008-04-03
ive figured out my problem.  there appears to be a bug in myth 0.21 where, when you resize the menu display it screws up the playback, even if you don't check off the button for use the same size for playback.  the workaround for this is to tell it to use a separate video resolution for playback.

---

### Post by tgm4883 on 2008-04-03
> **billionmonkeys said:**
> ive figured out my problem.  there appears to be a bug in myth 0.21 where, when you resize the menu display it screws up the playback, even if you don't check off the button for use the same size for playback.  the workaround for this is to tell it to use a separate video resolution for playback.

Link to this bug?  This doesn't seem to be the case for me

---

