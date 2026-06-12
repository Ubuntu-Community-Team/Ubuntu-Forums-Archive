---
title: "Can't get any video to play in firefox"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by net_vagabond on 2007-05-28
Please help me. I am having a huge problem, firefox won't play any video for me. I believe that I've installed the java and flash plugins and I know I installed the totem-xine plugin but none of the videos are working. Youtube doesn't, Veoh doesn't. It's very frustrating.

---

### Post by mshale on 2007-05-28
the best thing to do to test it is to disable Beryl if you are running that, use Metacity instead.  Also try and disable the Desktop Effects under system>>preferences.

---

### Post by net_vagabond on 2007-05-28
I am running metacity. I couldn't find "desktop effects". The only thing with desktop in it's name under preferences is for changing wallpaper.

Another note is that often, When firefox runs into a page with stuff it can't handle it just quits on me.

---

### Post by Datalanche on 2007-05-28
Youtube uses flash, which is a whole different beast. Try installing Adobe flash with package flashplugin-nonfree.

---

### Post by bytenram on 2007-12-11
> **Datalanche said:**
> Youtube uses flash, which is a whole different beast. Try installing Adobe flash with package flashplugin-nonfree.

OK, and where do we get this at?  I try going to a website that has flash and try installing the plugin through firefox and I get a message about not findinng flashplugin-nonfree

any ideas? 

thank you in advance for your help.

---

### Post by ImALittleTeaPot on 2007-12-12
don't download the flash player from a website. Get it from the synaptic package manager under the  button System-->Administration-->Synaptic Package Manager. Make sure that that under  System-->Administration-->Software Sources you have all the repositories enabled.

---

### Post by ImALittleTeaPot on 2007-12-12
Disregard my last post

The problem to this is stated in many other threads. Just found out that the new version of adobe flash hates gutsy, as in won't work. Uninstall all of your flash plugins, then go to the adobe labs site, install 9.0.64, if you can't find that, try installing 9.0.48, or really any version  previous to 9.0.115. The newest (9.0.115, which I believe is the one in the synaptic respository) won't work in gutsy.  That is why your flash won't play.

---

### Post by ozone702 on 2007-12-13
For days now I've been trying to fix this problem myself with no success.  I've finally got it working.

Here's what I did:

I went to System / Preferences / Sound.
I went to Sounds tab.
I changed Log in: to No sound.
I changed Log out: to No sound.
I re-booted.

When I went to YouTube.com, Firefox did not lock up when I played videos anymore.

NOTE:  Prior to this I tried everything I could find on these forums and others to resolve the issue with no success.  I'm new to Linux and Ubuntu but not to software development and I now know I did not fail to install necessary plug ins or drivers.  As a matter of fact, I turned the Log in back to what it was and re-booted to test whether videos locked up and as suspected they did.  So I'm certain this solved my problem.  Furthermore, I have had no problems for 2 days playing dozens of videos on YouTube and Break.com

I'm hoping this is a bug that can be identified and made known to everyone so this can be resolved and the community can move on.  Because this was a major hindrance to me using Ubuntu but not any longer.

Good luck,
  ozone

---

### Post by M34tw4d on 2007-12-15
Ozone:

I love you for posting that fix. I never would have figured that out, but it worked beatifully. It sounds completely ridiculous, btw. Thanks again.

---

### Post by whoboo on 2007-12-15
Bless you for posting that fix.  I have been bedeviled, so to speak, by sound problems for quite a while.  This fix fixed youtube.

Others still having problems will want to make sure their /etc/firefox/firefoxrc file looks like this

# which /dev/dsp wrapper to use
# FIREFOX_DSP="auto"
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

You don't need this line # FIREFOX_DSP="auto"
but I can verify using it makes firefox unstable and this fix allowed me to revert to aoss.

Thanks again. ... also my /etc/asound.conf file looks like

 pcm.my_card {
   type hw
   card 0
   # mmap_emulation true
 }
 
 pcm.dmixed {
   type dmix
   ipc_key 1024
    # ipc_key_add_uid false   # let multiple users share
    # ipc_perm 0666           # IPC permissions for multi user sharing (octal, default 0600)
   slave {
   pcm "my_card"
   #   rate 48000
   #   period_size 512
   }
 }
 
 pcm.dsnooped {
   type dsnoop
   ipc_key 2048
   slave {
   pcm "my_card"
#   #   rate 48000
#   #   period_size 128
   }
 }
 
 pcm.asymed {
   type asym
   playback.pcm "dmixed"
   capture.pcm "dsnooped"
 }
 
 pcm.pasymed {
   type plug
   slave.pcm "asymed"
 }
 
 pcm.dsp0 {
   type plug
   slave.pcm "asymed"
 }
 
 pcm.!default {
   type plug
   slave.pcm "asymed"
 }

[Can't remember why, but it made something work when I edited it.]

newbies would edit these files by opening a terminal window by clicking on the terminal icon and typing sudo gedit [file path and file name, e.g. /etc/asound.conf]

---

### Post by lespaul_rentals on 2007-12-15
```
sudo apt-get install ubuntu-restricted-extras
```

Should solve your problem right there.

---

