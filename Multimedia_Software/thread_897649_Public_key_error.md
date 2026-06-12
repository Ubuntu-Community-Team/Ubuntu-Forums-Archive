---
title: "Public key error"
date: 2008-08-22
forum: Multimedia Software
---

### Post by vegas588 on 2008-08-22
newbie trying to install some packages. When I do an update I get this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Does anyone know how to correct this? Running 8.04 new installation.

Thanks.

---

### Post by overdrank on 2008-08-22
> **vegas588 said:**
> newbie trying to install some packages. When I do an update I get this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Does anyone know how to correct this? Running 8.04 new installation.

Thanks.

Hi and welcome, if you added the medibuntu repo to your sources list then you can add the key look here
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by vegas588 on 2008-08-22
I am not so sure that worked.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
E: Some packages could not be authenticated
jamesc@hpubuntu:~$

---

### Post by Si-Ddevil on 2008-08-22
Make sure that in software sources you have hardy-proposed & hardy-backports enabled then try again

*edit*

have you entered this in the terminal?

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by ubuntu-freak on 2008-08-22
> **Si-Ddevil said:**
> Make sure that in software sources you have hardy-proposed & hardy-backports enabled then try again

*edit*

have you entered this in the terminal?

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

 
What does Hardy proposed and backports have to do with anything? I'd only recommend the backports repo anyway.
 
vegas588, take a look at my [how-to](ubuntuforums.org/showthread.php?t=766683) and see if part 1 helps at all. Saying that, the command to add the Medibuntu repo and key should be the same as in the link overdrank gave you.

---

### Post by vegas588 on 2008-08-22
That worked! I used the comprehensive multimedia page before and entered the same commands. I am thinking there was some kind of network trouble that kept it from working.

Thanks to all of you. I will continue with the rest of the recommended steps. there are so many media players available, which one is "the least trouble" for playing back standard dvd movies? vlc or mplayer?

---

### Post by ubuntu-freak on 2008-08-22
> **vegas588 said:**
> That worked! I used the comprehensive multimedia page before and entered the same commands. I am thinking there was some kind of network trouble that kept it from working.

Thanks to all of you. I will continue with the rest of the recommended steps. there are so many media players available, which one is "the least trouble" for playing back standard dvd movies? vlc or mplayer?

 
I recommend Totem and GNOME MPlayer for desktop videos, Gecko Media Player for streaming audio/video within a web browser, VLC for DVD playback, and either Rhythmbox, Exaile or Songbird (see part 5 of my howto) for desktop audio playback. You should certainly test out the latter, despite the fact it's pre-release, cos' it's just so promising and fun to use. Songbird uses the same engine as Firefox, namely Gecko, and you can even browse the web within it and search for music to listen to. I recommend the Pure White feather, or skin.

---

