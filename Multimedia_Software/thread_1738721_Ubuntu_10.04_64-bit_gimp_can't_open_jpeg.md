---
title: "Ubuntu 10.04 64-bit: gimp can't open jpeg"
date: 2011-04-25
forum: Multimedia Software
---

### Post by Wim Sturkenboom on 2011-04-25
Somewhere along the line I have managed to get the below error when loading a jpeg in the gimp (either with 'open with' on context menu or directly)

Running as an unprivileged user
```

Calling error for procedure 'file-jpeg-load':
Procedure 'file-jpeg-load' not found

Opening '/home/fortyfourgalena/Desktop/photos/liza/inkosanalodge_20061201/20061201_171151_PC010620.jpg' failed: Procedure 'file-jpeg-load' not found

```

Running as the 'main' user
```

Opening '/home/wim/Desktop/photos/liza/inkosanalodge_20061201/20061201_171151_PC010620.jpg' failed: Unknown file type

```

eye-of-gnome as well as gthumb image viewer are able to display the jpegs

This happens on a system running 10.04 / 64-bit. As I seem to recall a recent gimp update (might be wrong), I checked a 32-bit 10.04 laptop and it does not show the behavior. For information: the 64-bit system has some additional stuff installed for image processing (ufraw and darktable) but I have been using this already for a while without issues.

The other main change on this 64-bit system before I noticed the problem was the installation of a geforce 8400 video card including the 'nomodeset' option in grub and install of the latest driver from the nvidia website.

Can somebody verify that the gimp on a 64-bit system is still functioning.

Further a 'repair' from within synaptic throws the following error :(

```

E: /var/cache/apt/archives/gimp_2.6.8-2ubuntu1.2_amd64.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

```

I'm now going to do a complete gimp re-install from the repository but some feedback on the 64-bit is still appreciated as it might point me in the direction where it fails (and if I have to file a bug report).


Note:
I found some messages regarding this problem on the web but they were referring to older kernels ([noparse]2.6.8[/noparse]); and people reverted back to an even older kernel. And yes, there have been a recent kernel upgrade. Related?

---

### Post by Wim Sturkenboom on 2011-04-25
Did a complete removal of the gimp and after that an install; did not work. But the install now gave a little more clear error message about corrupted install file (in the apt cache).

Cleaned the cache completely and did the install (including gimp-ufraw) and now it works again :D

Maybe my HD is on it's way out :( No wonder with the amount of power outages over here and the numerous hard resets that I had to do when getting the 8400 card working (a couple of weeks ago).

---

### Post by Mander on 2011-05-19
I had this same problem on Fedora 13 after I messed around with some settings in GIMP.  I had two different settings directories, one referencing gimp 2.6 in my home folder, and another under /usr (I think?) that referenced 2.0.  I'm sorry but I failed to make a note of where this folder was, but I think it was an artifact of an old backup.

At any rate I finally fixed the problem by uninstalling everything that referenced GIMP, deleting all of the settings folders (making a backup first, of course!), and then reinstalling all of the GIMP stuff again.  I had previously tried just deleting the old folder and changing where GIMP looked for plugins etc., but it didn't work.  Deleting and reinstalling did, however.

---

