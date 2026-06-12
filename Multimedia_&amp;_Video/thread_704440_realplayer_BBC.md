---
title: "realplayer BBC"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by smakarl on 2008-02-22
Ubuntu is bringing computing to the world. The BBC brings news to the world.
Unfortunately the BBC, the best news coverage in the world, only does feeds via Realplayer. 

I have used the 3 installation methods found by searching ¨ realplayer deb ¨. none is totally realable. .. dpkg, synaptic, nor real.com .

The method from real.com , with user input during the installation, leaves possibility for operator error, & has no clean uninstall method.

What are the PROPER user responses for ¨installation directory / location ¨, & ´ symbolic link ¨, when using the real.com routine? 

Ubuntu should have tried & true installation routine in all releases for RealPlayer.

[email]smakarl@gmail.com[/email]

---

### Post by balticman on 2008-02-22
Maybe you should give up on realplayer.

I listen to radio  BBC via the firefox extention for MPlayer. It gives an error message when it first starts but after a few seconds the sound kicks in and continues without any problems. There are plenty of threads on these boards to help with this solution.

I havent managed to get the video streams working though.

---

### Post by nick_h on 2008-02-22
Yes, I also use the mplayer plugin for firefox to listen to the BBC.  For me it works for radio and video without a problem.  You need the select the Microsoft feed rather than the realplayer option.

---

### Post by ahaslam on 2008-02-22
You don't even need the plugin, just mplayer. An example of radio one:
```
mplayer rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra
```

---

### Post by MrClearPore on 2008-02-25
> What are the PROPER user responses for ¨installation directory / location ¨, & ´ symbolic link ¨, when using the real.com routine?

If you're installing **RealPlayer** from the .bin, run the installer as **root** and then just accept the defaults when it asks where to install the program and symbolic links.  That's how I used to do it when I installed RealPlayer with the .bin

Then I found a **.deb** package of RealPlayer that took care of the installation (but I had to set up the symbolic links on my own).

Now, I use the "nightly builds" from the real.com site [http://forms.helixcommunity.org/helix/builds/?category=realplay-current]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")
I first make a directory called **real** in my **/usr/local/** directory and then download/extract the appropriate **.tar** from the real.com link above into the **/usr/local/real** directory.
Next, I set up my symbolic links (this is for the Firefox browser):

```
sudo ln -s /usr/local/real/mozilla/nphelix.so /home/<user>/.mozilla/plugins
sudo ln -s /usr/local/real/mozilla/nphelix.xpt /home/<user>/.mozilla/plugins
```

Finally, I make a symbolic link that actually runs the RealPlayer itself:
```
sudo ln -s /usr/local/real/realplay /usr/local/bin
```

And that's it!  BBC plays fine this way.  This is a "nightly build" though.  There could be bugs, but I haven't had any problems using the method listed above.

A good reason to use the **.tar** extraction method is that you don't have to install the player itself.  To "upgrade" to another build, simply remove the contents of **/usr/local/real** and extract the new **.tar** to **/usr/local/real**.  Assuming the directory structure is the same from build to build. you won't have to re-link the **.so** and **.xpt** nor the **realplayer** binary.

Good luck.

---

### Post by vivabenfica on 2008-02-29
I had BBC Real Player problems as well. I could open the video only in Real Player stand alone (not embedded within firefox). I then installed vlc and mozilla-plugin-vlc and now I view quicktime and real player video within firefox.

---

### Post by gandaran on 2008-02-29
to me, the best plugin for real video or even wmv is the xine-plugin.
I replaced the totem plugin with the xine-plugin, works perfectly on bbc!

---

### Post by Nitro Fan on 2008-03-01
> **balticman said:**
> Maybe you should give up on realplayer.

I listen to radio  BBC via the firefox extention for MPlayer. It gives an error message when it first starts but after a few seconds the sound kicks in and continues without any problems. There are plenty of threads on these boards to help with this solution.

I havent managed to get the video streams working though.

Hi Balticman 
I have tried but cannot find a plugin for Mplayer for firefox can you send me a link please?

---

### Post by nick_h on 2008-03-01
> I have tried but cannot find a plugin for Mplayer for firefox can you send me a link please?
Use the mozilla-mplayer package in the repositories.
```
sudo apt-get install mozilla-mplayer
```

---

### Post by manish.rjn on 2008-03-01
I found this APT for an active repository:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

at the webpage: [http://www.kabatology.com/03/27/realplayer-for-ubuntu/](http://www.kabatology.com/03/27/realplayer-for-ubuntu/)

I tried and it worked perfectly and hassle free :-)

---

