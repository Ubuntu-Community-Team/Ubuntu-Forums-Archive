---
title: "Ubuntu newbie thinks he broke something bad in his audio setup..."
date: 2009-08-28
forum: Multimedia Software
---

### Post by Druegan on 2009-08-28
I'm hoping somebody can help me here.. 

A couple days ago, there was a large update through the update manager. For some reason I don't understand, it wasn't able to update everything?  It gave me the option for a partial update, and I went with that.  Everything seemed to work fine.

Then a day or so ago, I tried playing some movies I have on my hard drive.. none of them would work using the standard "Movie Player". mPlayer Movie Player would work..

Then Pidgin broke.. wouldn't connect to Yahoo's network, so I installed a couple others.. they wouldn't work either.. finally got connected again with Kopete. (i know this is sort of rambling, but I'm trying to reconstruct the things I did in hope it helps..)

About 3 hours ago, I wanted to mellow out with some Pink Floyd before I went to sleep.. So I tried to start Rhythmbox, and it wouldn't load..  it'd pop up and act like it was trying to load... but then it'd just quit. 

From there, I tried going into "Volume Control".. I could get the basic volume lever, but when I tried to open the mixer, it freaked out and gave me an error message. "No volume control Gstreamer plugins and/or devices found"..  then I kinda guess I compounded the problem..

I went into Synaptic, and did a search for "Gstreamer"... and selected to re-install everything that was marked as installed. It went through it's processes, no change.. soooo..

Trying to be a "good little newbie", I went to consult the almighty Google, with copied error message in tow.. did several searches.. and most of the forum bits I found referred me to the "Comprehensive Sound Problems Solutions Guide" (stickied at the top of these forums..)  And tried to blunder my way through it. I'm am still largely clueless of these things, but I try to fix bits...

It took me a while to understand what was up.. but I went through the ```
 sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
```
and then the
```
 sudo apt-get install gdm ubuntu-desktop
```
as recommended, as the previous did remove ubuntu-desktop..

I go back to check, using the "sudo modprobe snd-intel8x0" command.. which, I guess from the guide, is supposed to return some kind of thing saying "Yes, your ALSA driver is installed"...  but all I get is

druegan@Illuvatar:~$ sudo modprobe snd-intel8x0
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
druegan@Illuvatar:~$ 

So I google this, I read some forums.. apparently it's a bug or something.. or at least that's what I glean from what I read.. So I take it as an "everything's ok, I guess?".. as there wasn't any intelligible data in it..

I then type in " sudo nano /etc/modules"... and add "snd-intel8x0" to the end, like the guide suggests, and save.  

Now, here's where I get even more confused.. 

I reboot.. just to make sure everything's ok.. and to make sure all the bits are loaded..

System reboots fine, but upon trying to login to Ubuntu... I'm getting annoying beeping with every keystroke. It still logs me in just fine.. it just beeps when I type. Never did that before.  I also get the "ubuntu chime" bit when the desktop kicks up..  So I know I'm getting sound out of *something*...

But then I get this popup error message saying that "Volume Control can't be loaded" or somesuch.. with an option to try reloading, or not.  Trying reloading does nothing.. just brings the error message back.  And I can't get into Main Menu > System > Preferences > Sound.   It goes to load up, shows the "Starting Sound" bit up on the toolbar... but then just vanishes with nothing to show for it.. Like Rhythmbox and Movie Player did before.  

After this, I tried to experiment a little to see what worked and what didn't..  Rhythmbox still won't load, neither will Muine.. does the "trying to" bit up top and then disappears.

MPlayer loaded. When it did, I got this odd little thing I'd never seen before up on my toolbar, that identifies itself as "PulseAudio Applet"  So I clicked it.. and it's a volume control!  Which is cool.. but uh.. 

It shows 2 channels.. and I have 5...  and um.. it's using the wrong soundcard.  I have 2.. 1 is a Creative Labs *something*... I dunno, but it's old, and I haven't been using it. it's listed as "CA0106" on the "output devices" tab.. and it's playing, or at least the volume bit is bouncing in response to the test song I play in MPlayer.  The other one.. the onboard audio I *want* to use..  identified as "Nvidia CK804".. is silent.  So I click the thingy which sets it to default.

No change.   So I go forth into the Guide again, and I find this bit "Configuring default soundcards / stopping multiple soundcards from switching"  Sounds like what I need!  so I type:

"cat /proc/asound/modules"  and get the 2 names.. and they show up fine.. then I type:

"sudo nano /etc/modprobe.d/alsa-base" which comes up blank, but I guess it's supposed to?  and I add:

```
options snd-intel8x0 index=0
options snd-CA0106 index=1
```

And save, of course.  

And um.. nothing's really changed?  I'm kinda clueless at this point..so I'm going to reboot now just for grins.. But I still don't know why "Volume Control" is broken, or why I can't get into System>Preferences>Sound, or why Rhythmbox and Movie Player won't load...

Can someone please help me unbreak my system? Or at least let me know what info you need to come to the answer?  This was all working joyously up until the last big update.

Thanks much for any and all assistance, 
    Druegan


Ok.. I got it fixed.. I don't know what happened, or what I did.. but apparently somewhere in the mix the gnome audio controls stuff got uninstalled... not that I ever saw it do that..

But I uninstalled totem and Rhythmbox, reinstalled all Gstreamer plugins, reinstalled the gnome audio controls, rebooted, reinstalled totem, reinstalled rhythmbox, and all things work again.  Not the same way as they did before... but just as well, so I'm happy.

---

### Post by Druegan on 2009-08-28
I snipped this as it's no longer important.

---

