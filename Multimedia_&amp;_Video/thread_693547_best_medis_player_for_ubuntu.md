---
title: "best medis player for ubuntu"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by tavati on 2008-02-11
while installing mplayer it asks me for some ubuntu cd. i have internet and is it not possible to install without the ubuntu cd ??

---

### Post by jaytek13 on 2008-02-11
You have to remove cdrom as a source from synaptic. After doing so it will look to the internet for sources rather than the cd.

---

### Post by tavati on 2008-02-11
thankx but i am in kindergarden ubuntu. what is this synaptec ?

---

### Post by Dojan5 on 2008-02-11
In the system menu > Administration > Synaptic Package manager
In KDE (Kubuntu) it is called Adept, thus i guess you use Ubuntu, right?

---

### Post by Nerrep on 2008-02-11
Click System > Administration > Software Sources.

Type in the password, then untick the box in the 'Installable from CD-ROM/DVD' section. Ubuntu will then start looking for packages on the interwebs :)

---

### Post by tavati on 2008-02-11
thanks both of you!! i got it. now when i give command to install mplayer it gives me some error giving me names of 5 to 6 libs which are dependencies and says that these "cannot be installed" . what did i do ?

sudo apt-get install mplayer --fix-missing

then what i get ?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libpulse0 but it is not installable
           Depends: libungif4g (>= 4.1.4) but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages

so what did i do actually?? and what should i do now ??

---

### Post by Nerrep on 2008-02-11
Back in 'Software Sources', do you have the 'Universe' 'Restriced' and 'Multiverse' repositories ticked? They should be just above where you unticked the CD as a source.

---

### Post by tavati on 2008-02-11
i got it. i ticked all of them !!! :-) i played mplayer and opened one wmv file. although mplayer opened it but before that it gave one error : failed to open direct show codec wmvd--someting.dll . but it did not effect the playing of video file. after closing mplayer i got another error : gnome screensave or something error. but that also did nothing. i think something is still left. 

i don't know how to thank officially on this site. but thanks !!

---

