---
title: "Shotwell won't start"
date: 2012-11-01
forum: Multimedia Software
---

### Post by azertyfred on 2012-11-01
When I try to start Shotwell, nothing happens. I use PinguyOS Ubuntu 12.04 and the latest version of Shotwell. There's not even a dialog box with an error message, just nothing happens.
Also, I tried to reinstall the program, but this didn't work.
Any suggestions?
thx
fred

---

### Post by JR3 on 2012-11-04
Hi,
I have just joined to post the same thing.  However I decided to remove the installation that came with the Ubuntu install and installed from [http://yorba.org/shotwell/install.html](http://yorba.org/shotwell/install.html), following the binaries method.  

It appears to have installed, but  now I have no idea how to get it running !  No icons are added and although the Dash shows Shotwell Photo Manager it is rather inert, and does not respond when clicked.  I am not sure if it is a relic from the install I removed.  

When I search for shotwell it shows many files and folders, however if I check where they are located within their properties it shows:
inode/directory, which does not appear to exist when I go browsing for it.

Bit of a mystery...

---

### Post by gordintoronto on 2012-11-04
How did you install the latest version of Shotwell?

Try opening a terminal, and enter the command: shotwell

If there is an error, it should appear.

---

### Post by azertyfred on 2012-11-06
Thanks for the reponse, I typed 'Shotwell' in terminal and indeed there was an error message (missing library file). I opened synaptic but the missing file appeared to be installed. I then selected in synaptic the library file and marked it for reinstallation. Now it works again, thanks.

---

### Post by azertyfred on 2012-11-06
@JR3: try to install shotwell from synaptic, it's more clear I think. If you have the program 'ubuntu tweak' you can add shotwell to the software sources. It will then automatically update through the update manager. Good luck!

---

### Post by alfu on 2012-11-20
Shotwell was working fine in 12.04 LTS, but now, after spending hours tagging about 1,000  pix, it opens, shows a window of tagged pix, then promptly folds.  I had it set to write the meta data to the files, but even so, I am concerned that if I reinstall it, all the organizational file info relating to the pix will be destroyed.

Azertyfred, what was the name of the file you had to mark for reinstallation with Synaptic?

Update: I read somewhere that Shotwell gags on .MOV files, so I removed all these into a separate folder; still no improvement.  Shotwell stores its config files in 'home/.shotwell' (hidden folder: type <CTL>-h to see them in the home folder).

---

### Post by azertyfred on 2012-11-21
hi there, I'm not sure about the name of the library file I had to reinstall, but normally if you type 'shotwell' in terminal, you will get feedback in return. follow the instructions terminal gives you back. good luck!

---

### Post by alfu on 2012-12-02
Thank you, Azertyfred.  I should have thought of doing that.  At any rate, here is the result from that and I am still in the woods:

~$ shotwell
shotwell: tiffcomposite.cpp:1032: virtual uint32_t Exiv2::Internal::TiffMnEntry::doCount() const: Assertion `tiffType() == ttUndefined' failed.
Aborted (core dumped)

Re-installing Shotwell did not fix the problem.

Then I looked in Synaptic for any of these strings and found none.  So I upgraded anything with the string 'tiff' in the procedure name (all had '!' in the status flag).  On restart 'colord' folded, so I upgraded that, too.

Shotwell still bombs.

---

### Post by alfu on 2012-12-02
I then tried to re-install everything with a '!' in the status indicator, and since that is really tedious, stopped at F.  Not everything can be re-installed:
[FONT=Courier New]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_8.13-3ubuntu3.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_8.13-3ubuntu3.1_amd64.deb)
  404  Not Found [IP: 91.189.91.15 80][/FONT]

Shotwell still bombs.

It runs ok when I create a new user and run it from there.  I will just have to wipe it completely off the original user and re-install.  Fortunately all the tags are embedded in the .JPG files, and it should not disrupt anything done under the new user!

---

### Post by azertyfred on 2012-12-03
Good news for the jpg files, the issue with the flagged files was your major concern.
Again, I'm not an expert (far from that), but it looks like the issues are not situated in shotwell itself,
maybe you changed or upgraded the core recently?
'the failed to fetch' problem looks like a network problem
If you can fix the problem by installing another user, it means there was st wrong with the library/preferences files in your home folder and not with the program itself.
Anyway, hope everything works now.
Cheers

---

### Post by alfu on 2012-12-03
No, actually my main concern with Shotwell is that it folds a few seconds after launch, but I have about had it with Shotwell.

On another computer, with another set of photos, it is losing tags, and when I start the program, it spends a lot of time writing tags to photos, gets to 99% and loops constantly updating the last two photos.

Does anyone know of a more stable photo manager?

---

### Post by alfu on 2012-12-11
I found a workaround for Shotwell going into an endless loop writing tags to JPGs.  

Go to 'Edit/Preferences/Library/Metadata' and toggle the tag writing checkbox to off.  When you toggle it back on again, Shotwell will write the tags.  When it stalls at 99%, toggle the box again.

---

