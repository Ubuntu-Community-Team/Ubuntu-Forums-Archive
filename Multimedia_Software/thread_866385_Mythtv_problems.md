---
title: "Mythtv problems"
date: 2008-07-21
forum: Multimedia Software
---

### Post by dtgaynor on 2008-07-21
I recently installed a Hauppage WinTV-PVR 150 with the hopes of converting some VHS tapes to DVD. Mythtv seemed to be the way to go, so I downloaded the latest version from mythtv.org. I followed the instructions given by the mythtv-HOWTO html, got all the prerequisites installed, enabled all the repositories, and finally installed mythtv. Upon running myth-setup, I chose English as the language, but then received the message "No UPnP backends found". Then I went through the next two "Database Configuration" screens, and then received the message "cannot login to database?". After googling both messages and searching the forums, I couldn't figure out the problem, so I decided to remove mythtv and start over. I went into synaptics to remove the mythtv packages, but I found that they weren't even marked as installed. I tried to mark libmyth-0.21 for installation, but I received the following message:

"libmyth-0.21:
  Depends: libasound2 (>1.0.16) but 1.0.15-3ubuntu4 is to be installed"

So I tried installing it through the terminal with similar results.

I entered:

sudo apt-get update
sudo apt-get install mythtv

and got:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (>= 0.21.svn20080706-0.0) but it is not going to be installed
          Depends: mythtv-backend (>= 0.21.svn20080706-0.0) but it is not going to be installed
E: Broken packages

I then tried:

apt-get install mythtv-frontend

and got:

The following packages have unmet dependencies:
  mythtv-frontend: Depends: libmyth-0.21 (>= 0.21.svn20080706) but it is not going to be installed
E: Broken packages

then:

apt-get install libmyth-0.21

and got:

The following packages have unmet dependencies:
  libmyth-0.21: Depends: libasound2 (> 1.0.16) but 1.0.15-3ubuntu4 is to be installed
E: Broken packages

At this point I figured the problem had something to do with "libasound2" being outdated on my machine, but after several attempts to get a newer version, I managed to fail miserably, which is pretty much where I am now.

Admittedly I'm a total linux noob, so I tried to be as thorough as possible with this post. Any help is greatly appreciated!

---

### Post by wolfen69 on 2008-07-21
try
```
sudo dpkg --configure -a
```
then
```
sudo apt-get install -f
```
then try to install myth tv.

---

### Post by dtgaynor on 2008-07-21
hmmm when I did that I got:

The following packages were automatically installed and are no longer required:
  dkms dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 77 not upgraded.

so I did

```
apt-get autoremove
```

but I'm still getting the same errors after installing mythtv :(

Should I post the config.err file that I'm getting upon install? or is that normal... like I said: noob.

---

### Post by wolfen69 on 2008-07-21
you need to do
```
*sudo* apt-get autoremove
```

---

### Post by wolfen69 on 2008-07-21
i wanted myth tv, so i installed it in ubuntu. i could not for the life of me, get it to display live tv. so i decided to install mythbuntu instead. worked like a charm. i don't like the default xfce desktop, so i just installed the regular ubuntu-desktop on top of that. no problems now. just some food for thought.

---

### Post by dtgaynor on 2008-07-22
hmmm... still not working. I'll check into Mythbuntu though... thanks for your help!

---

### Post by jorbuntu on 2008-08-15
I ran into the same problem and fixed it.

I tried: > apt-get install mythtv-frontend
and got: > The following packages have unmet dependencies:
mythtv-frontend: Depends: libmyth-0.21 (>= 0.21.svn20080706) but it is not going to be installed
E: Broken packages

then I tried: > apt-get install libmyth-0.21
and got: > The following packages have unmet dependencies:
libmyth-0.21: Depends: libasound2 (> 1.0.16) but 1.0.15-3ubuntu4 is to be installed
E: Broken packages

Conclusion: The libasound2 version is should be at least 1.0.16 and is outdated

I fixed it by downloading the latest version from [http://packages.debian.org/sid/libasound2](http://packages.debian.org/sid/libasound2)

Installing the latest package solved the mythtv installation problem, and could run apt-get install mythtv-frontend smoothly.

Good luck!

---

### Post by eotakos on 2008-08-22
anyone still bothering with this thread?

what did finally happen with your case dtgaynor ?? you solved your problem? i had the same error messages, even though i installed mythtv directly through the repositories (i didn't bother with the packages from their site)

another thing is that the messages from apt-get are probably result of the fact that dtgaynor installed the packages without the help of apt-get / aptitude / dpkg ...  so these packages aren't declared to the lists of the package management tools...  really - how does anyone uninstall such packages??

---

### Post by markackerman8@gmail.com on 2010-03-23
Having the same problem with a new install of 9.10 and trying MythTV!! arghhh!, and the aforementioned libsound2 wouldn't install...anyone with a solution??

Not an ISSUE anymore

---

