---
title: "No Mpeg play plugins not found"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by phidia on 2007-10-25
I've been able to set this set up before-but following the sticky in this forum doesn't work.
Note the computer I'm attempting to do this on is NOT my regular desktop but has an up to date install of 7.04 
Following the sticky [here]("http://ubuntuforums.org/showthread.php?t=413624") completed all steps up to this point > [Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:

Code:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

/QUOTE]

trying to import the key as above -terminal outputs:
[QUOTE]gpg: no valid OpenPGP data found. 


Issuing xine-check I get this:

> [OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...


libdvd play and read IS installed so I'm not sure what happened.I mean if an update broke xine/totem somehow or what. It definately used to work. I have this "older" computer (with sempron2600 & 1Gb ram) connected thru HDMI to a 32" LCD TV. I kept up with updates but haven't checked video playback on it for a while.

---

### Post by earobinson on 2007-10-25
why not just use totem? Im pretty sure the package your looking for is the [ubuntu-ristricted-extras]("http://wiki.earobinson.org/index.php5?title=Ubuntu_Quick_Install#Restricted_Extras")

---

### Post by Qwerty_ on 2007-10-25
[https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796](https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796)

---

### Post by phidia on 2007-10-25
earobinson
Going to the link you provided-it appears that those links & programs all require Gutsy to work.
Thanks for the response and I'm trying to figure out why the sticky for feisty doesn't work and what broke video playback on my install.

---

### Post by phidia on 2007-10-25
> **Qwerty_ said:**
> [https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796](https://help.ubuntu.com/community/RestrictedFormats#head-6c1adf157cf1aaf47a391922036b3ecc98f01796)

Thanks I'm following that now :)

---

### Post by phidia on 2007-10-25
Thanks Qwerty, That worked and for anyone having a similar problem specifiically enabling[ Medibuntu]("https://help.ubuntu.com/community/Medibuntu") in source.list did the trick.
BTW I've done alot of configuration stuff with this particular install so I'm not ruling out that it's my fault that movie playback broke-just don't know.
I really appreciate the Ubuntu community tho-so thx for the help!

---

