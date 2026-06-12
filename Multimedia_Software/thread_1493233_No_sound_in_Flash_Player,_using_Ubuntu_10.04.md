---
title: "No sound in Flash Player, using Ubuntu 10.04"
date: 2010-05-25
forum: Multimedia Software
---

### Post by lkjoel on 2010-05-25
As the title says, there is no sound in Flash Player.

 

I have:

flashplugin-nonfree-extrasound      0.0.svn2431-3

flashplugin-nonfree                       10.0.45.2ubuntu1

flashplugin-installer

 

I also have gnash, klash, swfdec and some others.

 

Could you help me?

---

### Post by KrisWragg on 2010-05-25
Hi,

I just installed kubuntu 10.04 and I had the same problem, the only solution I could find that worked for me was to install a program called pulseaudio chooser which allowed me to select the stream that flash uses.

```
sudo apt-get install padevchooser
```

---

### Post by lovinglinux on 2010-05-25
Also having multiple plugins is not a good idea.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Also check of the PCM volume slider is all the way up.

---

### Post by lkjoel on 2010-05-28
I mostly use Google Chrome and Chromium.
I did install the FLASH-AID extension, since I do have firefox.
I did do it from the command line.
I also have another thread, in [Adobe Forums]("http://forums.adobe.com/thread/646473?tstart=0") (though last time I checked, there were 71 views and no replies).
Also, I just checked, and the sound globally doesn't work!
I did do a thread [here]("http://ubuntuforums.org/showthread.php?t=1481792") about the sound problems.

And thank you so much for trying to help!

---

### Post by Stormtrooper42 on 2010-06-05
I had no sound in Kubuntu 10.04 either.
The levels in alsa-mixer were correct, though.

```
sudo apt-get install pulseaudio pavucontrol padevchooser
```and then,

```
pavucontrol
```That's where the levels were wrong (analog output was muted).

---

### Post by lovinglinux on 2010-06-05
Try this:

[http://ubuntuforums.org/showpost.php?p=9214160&postcount=15](http://ubuntuforums.org/showpost.php?p=9214160&postcount=15)

---

### Post by Herofmb on 2010-06-08
I was having the same problem, every sound worked except for sound in flash.

It got solved after I've performed the last atualizations available.

Just that,

regards

---

### Post by triple.eh on 2010-06-17
> **Herofmb said:**
> 
It got solved after I've performed the last atualizations available.


Can you please clarify what "the last atualizations available" are and what steps you performed to get Flash sound in Firefox in 10.04LTS?

I'm experiencing the same issue and installed pavucontrol and padevchooser (pulseaudio package was already there).  I set the levels in pavucontrol as well as "alsamixer", but I still don't hear Flash sound.  System sounds and Rhythmbox work OK.

I appreciate your help, thanks!

--- UPDATE #1 ---
Re-installed Flash and Firefox plugin, rebooted, all is well!

--- UPDATE #2 ---
:frown: It only lasted one session:  I rebooted and Flash has no audio once again.

--- UPDATE #3 ---
I hope this is the last update post... :p

Executed the following to restore Flash audio in Firefox:
```

sudo aptitude purge adobe-flashplugin

```
Afterwards,
```

sudo aptitude install flashplugin-nonfree

```
:guitar:

---

### Post by lilychef on 2010-06-17
While trying stormtrooper's suggestion, I noticed  this:

pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.

I immediately aborted and ran apt-get-autoremove

It removed firefox - 3.5-branding

Flash audio now works again.  For now.  Ha!

---

### Post by lovinglinux on 2010-06-19
> **lilychef said:**
> While trying stormtrooper's suggestion, I noticed  this:

pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.

I immediately aborted and ran apt-get-autoremove

It removed firefox - 3.5-branding

Flash audio now works again.  For now.  Ha!

Weird.

---

### Post by lilychef on 2010-06-19
> **lovinglinux said:**
> Weird.

What's ***weird ***is that this is a completely new problem since four version upgrades of Ubuntu to which I've readily and immediately embraced.... and the fact that I finally, ECSTATICALLY got surround sound from Lucid, which initially made me jump for joy, now again leaves me again confounded...  It's frustrating:  I follow all the rules -- I upgrade when told to, I have new, supposedly compatible hardware, and consult the forums extensively before whining about some simple fix... But yet I still have problems getting simple things like AUDIO working.... I swear - if I didn't' have such hatred for the big boys, I'd suck up in a minute and go back to Windows (gulp - did I just say that evil word?) if I knew I could just click something and have it play properly....

Can I possibly be alone here?

---

### Post by liquido80 on 2010-06-20
I had no sound in flash (games, chrome browser, etc) after installing kubuntu 10.04. 
But this problem was solved when I installed pulse audio [COLOR="Blue"](apt-get install padevchooser)[/COLOR] :guitar:

---

### Post by Nerian on 2010-06-20
I also had no audio for flash videos after installing Kubuntu 10.04 yesterday, however the fix for me was to open kmix and raise the PCM volume which was defaulted to off.

Hope this helps,

[Link to where I explain the solution]("http://blog.deviantnode.com:50100/?p=79")

---

### Post by lkjoel on 2010-06-21
Actually, I solved it with this webpage: [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound").

I hope that this will help you too!

---

### Post by lbmounse on 2010-09-14
> Also having multiple plugins is not a good idea.

Install FLASH-AID extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture.

If you don't use Firefox or prefer to fix the problem from command-line, then see the Flash Optimization section of Firefox optimization and troubleshooting thread.

Also check of the PCM volume slider is all the way up.

Installing flash-aid and checking the PCM slider fixed it for me.  (On noticing PCM at 0, I probably didn't need flash-aid).

The PCM volume is in the mixer.  In Kubuntu, click on the speaker icon (system tray), and click mixer.  (It should be similar in Ubuntu) What was confusing was that the mixer did not appear at first, just a single volume slider.  I had to click on "mixer" again to see the full mixer.

(As an added bonus, the mixer allows me to adjust the volume of this laptop's two headphone jacks independently of eachother.)

---

### Post by fndtn on 2010-09-21
Ran into one variation when I upgraded from 10.04 to 10.10...

Noticed in Firefox, Tools -> Add-ons -> [Plugins] kept listing:

Shockwave Flash 9.0

While Software Center and Update Manager (and Synaptic Package Manager) all read:

Shockwave Flash 10.1 r85 (10.1.85.3-1maverick)

Opened Terminal

cd ~/.mozilla/plugins

ls 

libflashplayer.so   flashplayer.xpt          <----- Ah hah...the old Flash 9 components

:/usr/lib/firefox/plugins$ ls -latr
total 8
drwxr-xr-x 3 root root 4096 2010-09-21 18:40 ..
lrwxrwxrwx 1 root root   37 2010-09-21 18:48 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin   <--- The newer Flash 10...

cd ~/.mozilla/plugins
rm *

Back to Firefox - now the Plugins lists Shockwave Flash 10.1 r85

And sound works fine again.  (worked everywhere outside of Flash/Web).

</Doh!  moment>

---

### Post by seffyroff on 2010-09-26
This is broken for me too, tried everything above and no dice.  It has worked in the past, but it isn't now.

---

### Post by psi36 on 2010-10-10
Same problem here: sound on everything (including embeded .wmv) except Flash.

The thing is: before I had sound, in Flash and elsewhere but really low volume. When I put everything max it was barely audible.

Then I updated ALSA to the latest version using the script and instructions on [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

After that sound volume was as it should be, but Flash didn't have any sound anymore.

In Sound Preferences on the Applications tab nothing shows up when I'm playing a Flash movie.

Any hints on how to solve this?

---

### Post by psi36 on 2010-10-10
I tried the Flash purge and reinstall.

I use chromium, but checked in Firefox if there weren't two version of Flash plugin installed and there weren't.

I tried about everything I could find here on the forum, but nothing works.

---

### Post by pixatintes on 2010-11-14
> **lovinglinux said:**
> Also having multiple plugins is not a good idea.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Also check of the PCM volume slider is all the way up.

Thank you ... fanstastic extension. It works for me.

---

### Post by lkjoel on 2010-11-14
> **psi36 said:**
> I tried the Flash purge and reinstall.

I use chromium, but checked in Firefox if there weren't two version of Flash plugin installed and there weren't.

I tried about everything I could find here on the forum, but nothing works.
Even OSS?

---

### Post by sirpy on 2011-09-15
what worked for me was to have the following in .asounrc
(add comments to the previous asoundrc and add the pcm default stuff )
#pcm.pulse {
#type pulse
#}
#ctl.pulse {
#type pulse
#}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

---

