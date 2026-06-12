---
title: "Major failure of software Management."
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by redpepper on 2007-06-30
:confused: Totem Movie player wont play dvd.  Said to install appropriate plug-ins.  I followed the help instructions and wound up in the universe and multiverse area called _medibuntu_ (ohh brother!!).   I typed in 4 lines of code at the terminal, entered the password and received nothing but error boxes in Sympatic Package Mgr. and Add Remove Applications. 

 Such as:  _failed to check for installed and available applications _ 

                        Cache->open() failed, Please report.

                         The list of sources could not be read

                         Type 'The' is not known on line 1 in source list /etc/apt/sources.list d/medibuntu. 

I am a new user with a Dell installation of Ubuntu on a new XPS-410 with Intel Core 2 duo and 2 gigs of ram.

Canonical wont touch it as it is not supported.  If I un/reinstall Fiesty, could this be a solution??

Any help will greatly welcomed.

---

### Post by neoguy2012 on 2007-06-30
Hi,

I just followed what they said on [www.ubuntuguide.org:](www.ubuntuguide.org:)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

Basically, try this out:
```

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

sudo apt-get install libdvdcss2

```

good luck!

---

### Post by ausmuso on 2007-06-30
No need to uninstall Feisty, you can get perfect DVD playback with it.
Did you really follow the instructions on how to add Medibuntu to your APT sources list? You can do it in two ways: either edit your /etc/apt/sources.list file manually (as super user), or add Medibuntu using the Synaptic GUI.
Once you've done this, do a "sudo apt -get update" and the Medibuntu packages will be added to your list.

Hint: there is an alternative: download the VLC player from the Universe repository. It will play anything and it comes complete with all the codecs and libraries you need.

Ausmuso

---

### Post by redpepper on 2007-06-30
Thank you for your response.  I am a new computer user to the command line.  The entire Synaptic Package Mgr. is completely blocked with the error box-cant get inside it.  

How do I edit manually as super user?  (My ignorance is _not_bliss)

---

### Post by ausmuso on 2007-07-01
> **redpepper said:**
> Thank you for your response.  I am a new computer user to the command line.  The entire Synaptic Package Mgr. is completely blocked with the error box-cant get inside it.  

How do I edit manually as super user?  (My ignorance is _not_bliss)

open a terminal and type: "sudo gedit". Ubuntu will ask for your password. It will then open the text editor in superuser mode and you can edit any file you like. Open /etc/apt/sources.list and add, at the bottom of the list:

## Medibuntu
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Save the file.

also see: [http://ubuntu.wordpress.com/2005/12/](http://ubuntu.wordpress.com/2005/12/), halfway through the issue. Note there you've also got to get the Medibuntu gpg key otherwise you'll keep getting warning messages.

Better still:

Read thread [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Good luck!
Ausmuso

---

