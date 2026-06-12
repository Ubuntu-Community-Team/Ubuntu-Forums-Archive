---
title: "Flash not working in Kubuntu 9.04 64bit"
date: 2009-05-23
forum: Multimedia Software
---

### Post by Wired84 on 2009-05-23
Hi,

Been using linux for several years now and recently switched to ubuntu, and then yo kubuntu as I prefer the KDE interface.

I installed Kubuntu a few days ago on 8.04. But was having trouble getting flash working on any browser. After much messing about and googling, it still would not work.
I decided to try and upgrade to 9.04 to see if that would help.

Whilst I was upgrading I was using the internet and when it was just about fully upgraded, flash started working.
Unfortunatly it was fully upgraded by then so could not go back.
Rebooted into kubuntu 9.04 (which is awesom btw) tried flash and no luck.
I purged the restricted extras packages and removed anything to do with flash, rebooted and reinstalled all these using 

apt-get install ubuntu-restricted-extras kubuntu-restricted-extras sun-java6-plugin xubuntu-restricted-extras
also installed the adobe 64bit flash plugin 

Went back into firefox, went onto youtube and it appears to work but get a blank cream box where the video should be.
Tried this on Konqueror and get nothing atall, the video box is missing.

Anyone have any ideas? How can I remove java and flash completely so I can try and reinstall. Or is there another way to get this working?

Thanks in advance

---

### Post by gandaran on 2009-05-23
you should install only the kubuntu-restricted-extras-packages not the ubuntu-restricted-extras and xubuntu-restricted-extras packages if you are using only kubuntu, this will only add up to the mess.
and if you installed the 64-bits adobe flash manually don't forget the restricted extras package also installs the 32-bits adobe flash flashplugin-nonfree package which you must remove or firefox wont work with the 64-bits flash.

---

### Post by Wired84 on 2009-05-23
That might be it, how can i uninstall everything to d with flash? then once iv reinstalled kubuntu restrited extras how to i remove the 32 bit adobe flash?

---

### Post by gandaran on 2009-05-23
> **Wired84 said:**
> That might be it, how can i uninstall everything to d with flash? then once iv reinstalled kubuntu restrited extras how to i remove the 32 bit adobe flash?
use synaptic package manager, look up those packages or type flash in search box, you should see the restricted packages and flashplugin-nonfree or flashplugin-installer package, mark the packages for complete removal then click the apply button.
also remove the nspluginwrapper package.

---

### Post by Wired84 on 2009-05-23
Right, well I removed the restricted extras packages and it worked, installed just the kubuntu one and its stopped working. 
Any idea or what file I need to remove to get flash working as well as mp3 etc?

---

### Post by Wired84 on 2009-05-23
Scratch that, sorted it!!

Was the nsplugin that stopped it working. Thanks guys!!

---

### Post by gandaran on 2009-05-23
> **Wired84 said:**
> Right, well I removed the restricted extras packages and it worked, installed just the kubuntu one and its stopped working. 
Any idea or what file I need to remove to get flash working as well as mp3 etc?
keep the kubuntu package installed, remove only flashplugin-nonfree or flashplugin-installer packages or both if installed.

---

### Post by gandaran on 2009-05-23
> **Wired84 said:**
> Scratch that, sorted it!!

Was the nsplugin that stopped it working. Thanks guys!!
no, when you remove nspluginwrapper it also removes the flash dependencies.

---

### Post by benvantende on 2009-05-26
Heyla,

I still have issues with some flash content that does not work and just does not show with 64bit. Stuff like YouTube etc just works. For instance on this site: [http://www.coda-apeldoorn.nl/](http://www.coda-apeldoorn.nl/) There should be a whole site wide dynamic flash banner underneath the header. Maybe it is the fact that it is dynamic that does not make it work with 64bit. The other example I have is [http://zoeken.mijngelderland.nl/?q=Arnhem](http://zoeken.mijngelderland.nl/?q=Arnhem). In the left there should be a flash browser. These things work on my Ubuntu 32 bit.

gRTz

ben

---

### Post by Wired84 on 2009-05-29
> **gandaran said:**
> no, when you remove nspluginwrapper it also removes the flash dependencies.

Well it does seem to work now! What do I have to reinstall to keep dependancies?

---

### Post by benvantende on 2009-06-15
I just recently install Firefox 3.5b4. That solved everything for me concerning animated flash not showing on Kubuntu 64bit.

gRTz

ben

---

### Post by RKilbride on 2009-06-15
I went to this website, typed in what they suggested in terminal and got my flash working on 2 machines that would not losd flash at all ....

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

---

