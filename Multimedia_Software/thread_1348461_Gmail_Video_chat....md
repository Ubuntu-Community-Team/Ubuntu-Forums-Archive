---
title: "Gmail Video chat..."
date: 2009-12-07
forum: Multimedia Software
---

### Post by pulikkottil on 2009-12-07
How can I use Gmail Video chat in Ubuntu 9.10?
Regards,
 Pulikkottil:KS

---

### Post by gradinaruvasile on 2009-12-07
Here it is how you get it working:

Install Pidgin from this repository:

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Open a terminal (applications -> accessories -> terminal) and type (copy-paste better):

sudo gedit /etc/apt/sources.list

Add the following line to the end of the file:

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

Then type:

sudo apt-get update && sudo apt-get dselect-upgrade

Start Pidgin, select tools -> plugins, tick the Voice/Video Settings plugin, select configure:

Output Plugin: Pulse (if u use ALSA specifically, select ALSA, but by default Ubuntu 9.10 uses PulseAudio)
Input Plugin: Pulse
Both devices default.

Video (this is mandatory to use camera !):

Output Plugin:  X Window ... (xv) (or whatever you prefer, i found that id i left these to default values sometimes they wouldnt work)

Input:
Plugin: Video4linux or Video4Linux2 or whatever setting you have that permits selection a device other than "default" (usually "pc camera" if you have a detected webcam)

You must select on both ends a camera  - or, if not available, you MUST specify "Test Input" plugin! Videochat will not work if on one end you dont have an explicitly set video input device!

So, set up the plugin, log in with the gmail account, right click on the contact you want to call, select Audio or Audio/Video call (when and if available).

I tested this Pidgin version with audio chat with the Windows GTalk client. It worked. 
IT DID NOT WORK with video calls: - despite the fact that both computers had working video cameras, on the right-click drop down list i only had the audio call (and not the audio/video) option available when calling the contact logged in with Windows GTalk client. The audio call that was available worked. It may be that i did not set up the webcam properly on the Windows client (Windows 7 BTW), but i had no options for it either.

Tips:

- To see what option works for your webcam, press alt+f2 and type:

gstreamer-properties

Press enter.
Go to the video tab, and play with the settings - you have a test button there, it will open a window (when set to the correct settings) that shows your webcam image (make sure no program is running that uses the webcam). 
The same options are available in the Pidgin plugin settings so its easy to find out your webcam settings.

- Must have settings:

If you want video chat over gmail (at least Pidgin to Pidgin works well) and only one side has webcam, the other side MUST set its video input plugin to "Test Input" - otherwise the communication will crash (at least in my experience).

What i tested and what worked for me:

- Pidgin - Gtalk (on Windows) - audio call worked, video did not (did not even had option for it). I dont know why, maybe some webcam settings in Windows 7 i dont know about.
- Pidgin (Ubuntu 9.10) - Pidgin (Ubuntu 9.04) - Both video and audio call worked  - gmail to gmail accounts + local XMPP server (OpenFire) accounts.

---

### Post by batarce on 2009-12-26
what should I do if I have pidgin already installed?

---

### Post by gradinaruvasile on 2009-12-26
The same. Add the repository and then open the update manager, click check. You should get a list of upgrades - pidgin and other stuff such as gstreamer. Do the update and you are set. Do not forget to setup the plugin and tell the other guy to do the same, otherwise it wont work..

---

### Post by batarce on 2009-12-26
I got this message 

WARNING: The following packages cannot be authenticated!
  libpurple-bin pidgin-data

---

### Post by gradinaruvasile on 2009-12-26
No problem with those. 
Copy-paste the following in a terminal:

```
gpg --keyserver keyserver.ubuntu.com --recv A1F196A8
gpg --export --armor A1F196A8 | sudo apt-key add -
```

This will add the Pidgin Dev PPA's key to your keyring.

---

### Post by batarce on 2009-12-26
Are Pidgin and Pidgin Internet Messenger  the same? For some reason my Pidgin Internet Messenger does not open after I have added the repository you have suggested and updated it.

I have not done this typing yet

gpg --keyserver keyserver.ubuntu.com --recv A1F196A8
gpg --export --armor A1F196A8 | sudo apt-key add -

---

### Post by gradinaruvasile on 2009-12-26
Use copy-paste. Its faster ;).

Open a terminal and type:

pidgin

and press enter. What happens? If there is some error message, copy-paste it here.

---

### Post by batarce on 2009-12-26
:~$ pidgin
The program 'pidgin' is currently not installed.  You can install it by typing:
sudo apt-get install pidgin
bash: pidgin: command not found

---

### Post by gradinaruvasile on 2009-12-26
Thats a bit obvious... You dont have pidgin installed.

Type in a terminal:

sudo apt-get install pidgin

as suggested.

---

### Post by batarce on 2009-12-26
but why the pidgin internet messenger is not running any more? It was before.

---

### Post by batarce on 2009-12-26
> **gradinaruvasile said:**
> Thats a bit obvious... You dont have pidgin installed.

Type in a terminal:

sudo apt-get install pidgin

as suggested.

I did that and I got

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libgtk2.0-0 (>= 2.18.0) but 2.16.1-0ubuntu2 is to be installed
          Depends: libpurple0 (>= 1:2.6.0) but it is not going to be installed
          Depends: libstartup-notification0 (>= 0.10) but 0.9-1 is to be installed
          Depends: perl (>= 5.10.0-24ubuntu4) but 5.10.0-19ubuntu1.1 is to be installed
E: Broken packages

---

### Post by gradinaruvasile on 2009-12-26
What Ubuntu version do you have? It seems to be 9.04. I have it too and it works for me. I think you added the karmic (9.10) version PPA.

In a terminal type:

cat /etc/apt/sources.list

Copy-paste the result here.

Edit: wrap it in CODE tags to make it more easy to read.

---

### Post by batarce on 2009-12-26
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

---

### Post by gradinaruvasile on 2009-12-26
As i said... The last line is wrong.
It should be:

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) [COLOR="Red"]jaunty[/COLOR] main

In a terminal:

sudo gedit /etc/apt/sources.list

Correct the last line replacing karmic with jaunty. Save it. Then quit and type:

sudo apt-get update && sudo apt-get install -f && sudo apt-get dselect-upgrade

---

### Post by batarce on 2009-12-26
It seemed that it updated, but pidgin still not running

---

### Post by gradinaruvasile on 2009-12-26
> **batarce said:**
> It seemed that it updated, but pidgin still not running

Did you install it?

sudo apt-get install pidgin

---

### Post by batarce on 2009-12-26
Great. Finally my pidgin has been updated. Thanks!!!

---

### Post by gradinaruvasile on 2009-12-26
See in the screenshots my config of the audio/video plugin (tools -> plugins).
Also look closely at my long post about the configuration principles.

---

### Post by stevo1977 on 2010-01-15
Grad, thanks for the very helpful post(s).  I seem not to have the Voice/Video option (the plugins list jumps straight from the "Text" one to "XMPP").  Any idea why that would be the case?  I'm running Pidgin 2.6.5.  Thanks again.

---

### Post by dreamersword on 2010-02-01
I couldn't get video to work from pidgin to a windows gmail client until I went and installed gstreamer0.10-plugins-ugly-multiverse. I got the suggestion from the Empathy FAQ [http://live.gnome.org/Empathy/FAQ#Audio_and_Video_calls](http://live.gnome.org/Empathy/FAQ#Audio_and_Video_calls) It made both my Empathy and pidgin work.

---

