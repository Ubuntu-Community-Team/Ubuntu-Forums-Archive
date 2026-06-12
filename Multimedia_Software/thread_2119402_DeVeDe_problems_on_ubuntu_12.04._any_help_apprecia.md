---
title: "DeVeDe problems on ubuntu 12.04. any help appreciated"
date: 2013-02-23
forum: Multimedia Software
---

### Post by brokeit on 2013-02-23
im having trouble with DeVeDe.

its only creating and converting one movie to an iso image ready to be burned.
when i want to create multiple movies to one dvd disk.

on other occasions i try to create a DVD with multiple movie files on it i get this error messgae:

Conversion Failed.
Seems to be a bug of mencoder !!

im trying to create a DVD with four different movie titles. i also make sure i click the button to make sure it all fits to a 4.7GB DVD disk.
ive used devede many times before, on my old laptop. with no significant problems.

but each time i try to create a DVD using devede containing more than one movie file.
  it fails and gives me this error message:

 Conversion Failed.
Seems to be a bug of mencoder !!


id really appreciate so help here please. Im still relatively inexperienced using ubuntu. so i apologize for not being able to explain or give any more concise details at this time. please do not hesitate to ask me any questions. i will try to answer them as clearly as possible.

im using Ubuntu 12.04 LTS
on an old amd +2400 box.

can anyone tell me why i might be having the above issues ?
how do i find out what bug in mencoder is causing the problems ?

---

### Post by speartip on 2013-02-24
Hi. I had the same issue. This is what solved it for me.
Update to a latter ffmpeg, by adding this ppa & updating.
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
Then I uninstalled devede & got a later version from here:
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)
Set the encoders to ffmpeg in preferences & you should be good to go.

---

### Post by brokeit on 2013-02-24
hi speartip.

thanks for your reply.

im having problems adding the PPA you suggest to my system. using the below.
**Adding this PPA to your system**

                            You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:jon-severinsson/ffmpeg**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help-soyuz/ppa-sources-list.html")) 



im unsure what the correct command is i need to use to add this PPA.
can you post me the right command i need to use to add this PPA to my system?


i have tied:


sudo add-apt-repository ppa:jon-severinsson/ffmpeg 


is this the correct command i should be using to add the PPA for ffmpeg to my system and software sources??




 a few but i get this error messages:mark@mark-desktop:~$ sudo add-apt-repository ppa:user/ppa-name ppa:jon-severinsson/ffmpeg
[sudo] password for mark: 
Error: need a repository as argument
mark@mark-desktop:~$ sudo add-apt-repository ppa:ppa:jon-severinsson/ffmpeg 
Cannot access PPA ([https://launchpad.net/api/1.0/~ppa/+archive/ppa](https://launchpad.net/api/1.0/~ppa/+archive/ppa)) to get PPA information, please check your internet connection.
mark@mark-desktop:~$ sudo add-apt-repository ppa:jon-severinsson/ffmpeg 
You are about to add the following PPA to your system:
 Updated FFmpeg packages, including dependencies.

Note: This PPA depends on some packages found in the official backports repository.  Please enable it before adding this PPA to your sources.

Please note that this is *actual* FFmpeg, from ffmpeg.org.
Recent Debian and Ubuntu packages feature Libav (from libav.org), a prominent FFmpeg fork, instead.  You should be safe upgrading from Libav to FFmpeg, as the FFmpeg developers regularly pull from the Libav git tree, and thus have all Libav features, as well as several of their own.

However, both Libav and FFmpeg periodically break backward compatibility in order to more easily provide new features, so applications built against one version will not always work with the next.  To confuse matters further, the version numbers of Libav and FFmpeg are not enough to tell if they are compatible, to find out one has to dig in the source code.  To summarize my findings so far: FFmpeg 0.7 is backward compatible with FFmpeg 0.6 and 0.5, as well as Libav 0.6 and 0.5; FFmpeg 0.10 is backward compatible with FFmpeg 0.8 and 0.9, as well as Libav 0.7 and 0.8; while FFmpeg 0.11 is not backward compatible with any priorly released FFmpeg or Libav versions.

For lucid (10.04) through oneiric (11.10) this PPA provides both FFmpeg 0.10 and (part of) FFmpeg 0.7.  The `ffmpeg` source package provides shared libraries, development files, and executables from FFmpeg 0.10, while the `ffmpeg-oldabi` source package provides the shared libraries from FFmpeg 0.7.

For precise (12.04) and quantal (12.10) this PPA only provides FFmpeg 0.10, as Ubuntu no longer contain any packages depending on the old ABI.
 More info: [https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
Press [ENTER] to continue or ctrl-c to cancel adding it

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer



im using 12.04 LTS.

---

### Post by speartip on 2013-02-24
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
```
then:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by brokeit on 2013-02-24
ive used those commands and rebooted.

ill try to create another dvd using devede now to see if the probs i was having have now been rectified.

ill post back when i know for sure.

---

### Post by speartip on 2013-02-24
> **brokeit said:**
> ive used those commands and rebooted.
You may need the Backports repo enabled for it to work, apparently it takes some packages from there.
I also add the medibuntu repository & make sure I have the restricted extras installed.
2 of the 1st things I do on  a fresh install.
I'm using 12.04 too, & the ffmpeg ppa works fine on my machine.

---

