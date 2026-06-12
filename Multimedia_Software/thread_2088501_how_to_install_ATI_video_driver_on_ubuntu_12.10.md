---
title: "how to install ATI video driver on ubuntu 12.10"
date: 2012-11-26
forum: Multimedia Software
---

### Post by MRxSNIPES2 on 2012-11-26
I am trying to help my friend install his video driver but I never used ATI so I need help where and or how do I get the diver for Advanced Micro Devices [AMD] nee ATI Broadway [ATI Mobility Radeon HD 6800 Series].
I tryed the one is the Ubuntu Software Center but did not work.
he us using a laptop. thanks for any help you can give

---

### Post by simonmoon42 on 2012-11-26
Isn't catalyst showing up under "additional drivers"?

---

### Post by MRxSNIPES2 on 2012-11-26
additional drivers was not on the system so I installed it and it not showing up
what is going on I never used Ubuntu 12.10

---

### Post by simonmoon42 on 2012-11-27
> **MRxSNIPES2 said:**
> additional drivers was not on the system so I installed it and it not showing up
what is going on I never used Ubuntu 12.10

If you go to the dash (top left on the launcher menu or press the super/windows key) and type "drivers" it should come up.

---

### Post by MRxSNIPES2 on 2012-11-27
no. nothing come up

---

### Post by simonmoon42 on 2012-11-27
You can download the driver here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Once it is installed you should be able to find it in your dash by typing "catalyst".

---

### Post by MRxSNIPES2 on 2012-11-27
OK download it just give me a error.
I uploaded the pic to my website
[http://184.17.108.15/ati/](http://184.17.108.15/ati/)

---

### Post by simonmoon42 on 2012-11-29
> **MRxSNIPES2 said:**
> OK download it just give me a error.
I uploaded the pic to my website
[http://184.17.108.15/ati/](http://184.17.108.15/ati/)

I wasn't able to open that website. Please attach it to your next post.

---

### Post by unplugged23 on 2012-11-30
I'm having a similiar issue, and thought it might be more appropriate to post it here rather than opening a new thread. I recently installed 12.10 on an HP laptop with an amd 4650. I installed steam (their new beta client for linux) and downloaded tf2. The game suffered poor performance, and I realized I hadn't installed the propietary video drivers. I went to check additional drivers, but it just said that no additional drivers were in used, and displayed no options to install catalyst. I installed it manually through terminal, but when I rebooted Unity would not load. I reverted back, and installed KDE to try the drivers there. With KDE after a reboot, I could not get the screen resolution to set properly; also using KDE kind of defeats the purpose, because I need to be running unity in order to use the native steam client. I even downloaded the driver straight from amd's site, built the package and had the same issue. Wondering if there's anything I can do to solve this issue? Let me know if you need anymore information from me, and thanks for any help!

---

### Post by Yellow Pasque on 2012-11-30
> **unplugged23 said:**
> I recently installed 12.10 on an HP laptop with an amd 4650.
The proprietary fglrx/Catalyst driver no longer supports your card and older versions won't work on Ubuntu 12.10. [https://bugs.launchpad.net/bugs/1058040](https://bugs.launchpad.net/bugs/1058040)

> Wondering if there's anything I can do to solve this issue? Let me know if you need anymore information from me, and thanks for any help!
Use Ubuntu 12.04 and install the "legacy" driver: 
[http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip)

---

### Post by unplugged23 on 2012-11-30
> **Temüjin said:**
> Use Ubuntu 12.04 and install the "legacy" driver: 
[http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip)

Cool, makes me sad to have to downgrade, but thanks for the help!

---

### Post by MRxSNIPES2 on 2012-12-01
> **Temüjin said:**
> The proprietary fglrx/Catalyst driver no longer  supports your card and older versions won't work on Ubuntu 12.10. [https://bugs.launchpad.net/bugs/1058040](https://bugs.launchpad.net/bugs/1058040)


Use Ubuntu 12.04 and install the "legacy" driver: 
[http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip)


I tryed that and hopeing it will help and still got the same error here is here is the new link sorry for the bad one last time
[http://184.17.118.11/ati/](http://184.17.118.11/ati/)

---

### Post by MRxSNIPES2 on 2012-12-02
> **Temüjin said:**
> The proprietary fglrx/Catalyst driver no longer supports your card and older versions won't work on Ubuntu 12.10. [https://bugs.launchpad.net/bugs/1058040](https://bugs.launchpad.net/bugs/1058040)


Use Ubuntu 12.04 and install the "legacy" driver: 
[http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip)

i try this hopeing it will work but i got the same error here is the link sorry for the last bad one
[http://184.17.118.11/ati/](http://184.17.118.11/ati/)

---

### Post by MRxSNIPES2 on 2012-12-02
Sorry for reposting I am not seeing the new post so I am not going to use QUOTE
I try this hopeing it will work but I got the same error here is the link sorry for the last bad one
[http://184.17.118.11/ati/](http://184.17.118.11/ati/)

---

### Post by Yellow Pasque on 2012-12-02
@MRxSNIPES2:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
sudo apt-get install lib32gcc1 #Use this command only if running 64-bit
cd ~/
wget http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip
unzip http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip
chmod +x amd-driver-installer-12.6-legacy-x86.x86_64.run
sudo sh ./amd-driver-installer-12.6-legacy-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
```

---

### Post by MRxSNIPES2 on 2012-12-02
> **Temüjin said:**
> @MRxSNIPES2:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
sudo apt-get install lib32gcc1 #Use this command only if running 64-bit
cd ~/
wget http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip
unzip http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip
chmod +x amd-driver-installer-12.6-legacy-x86.x86_64.run
sudo sh ./amd-driver-installer-12.6-legacy-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
```

ok i got it installed but now it get a new error
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following. 
 
No AMD graphics driver is installed, or the AMD driver is not functioning properly. 
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

---

