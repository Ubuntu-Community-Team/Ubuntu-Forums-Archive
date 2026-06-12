---
title: "Updating Ubuntu lost my network drivers"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by Sammel on 2012-03-23
I am using Ubuntu 10.04. Motherboard is Asus M5A87.

After installing some updates my internet connection stopped working. (Nothing works, can't get IP from DHCP, can't ping any ip) Ubuntu says that no Network card is detected.

My internet connection is fine, from other OS on my computer there is no problem.

Similar thing has happened to me earlier when installed updates.
(Then internet connection didn't die completely, it only lost connection randomly.)
Back then I fixed it by following this advice:
> 
Run: sudo lspci -v

It will show both the name of your NIC and the driver that is being used. Then, research (usually at the company that made the NIC website) what driver that NIC is supposed to use for Linux. In my case, I found that they were different and, after I installed the correct driver, my internet connection became stable.

Install Driver root sh autorun.sh

That is the same NIC my PC has and the same (wrong) driver that Ubuntu chose. So, you need to download driver r8168 for Linux from Realtek Taiwan. Follow the instructions to make the new driver module. Once the new module is built, do the following as root:

1) sudo su (to become root)
2) depmod -a
3) Edit /etc/modprobe.d/blacklist.conf
Add a new line containing: blacklist r8169
Save the file.
4) Edit /etc/initramfs-tools/modules
Add a new line containing: r8168
Save the file.
5) update-initramfs -v -u -k `uname -r`
(Note that in the preceding command, those are NOT quote marks. They are grave accents, on the key to the left of the 1 key above the alpha keyboard.)
6) reboot
 

This time that didn't help.
What should I do to fix my internet connection?

---

### Post by ChrisLancs on 2012-03-23
I recently had trouble with a wireless pci card the default ubuntu driver wouldnt run it and i couldnt get the card to come up.

My card is a ralink card and i found linux drivers on their website, I had to build them from source but it did fix my issue, maybe your wifi manufacturer has linux drivers you can compile.

I too had to run through all of the blacklisting of the default modules etc.

Edit: also run sudo lspci -v just to check your driver is being picked up, if it is then try and modprobe it see if that brings up the card, if it does then its likely you have a typo in the edit.

---

### Post by Sammel on 2012-03-23
My connection is normal Ethernet, not wireless.

I tried downloading new drivers from manufacturers site but they didn't help or installation didn't work.

This is what I get when trying to install drivers I downloaded:
> th@gaidin:~/Työpöytä/Verkon korjaus/r8168-8.028.00$ sudo sh autorun.sh 
Check old driver and unload it.
Build the module and install
make[2]: *** Kohteen "korjaus/r8168-8.028.00/src" tuottamiseen ei ole sääntöä. Seis. (This translates to: "No rule to produce target korjaus/r81... Stop"
make[1]: *** [clean] Virhe 2 (This means: Error 2)
make: *** [clean] Virhe 2



---

### Post by Sammel on 2012-03-23
Also, is there way to make sure that this wont happen again next time I install updates?

---

### Post by chili555 on 2012-03-23
Can you open the package manager Synaptic and verify that you have installed *build-essential* and *linux-headers-generic*?

---

### Post by Sammel on 2012-03-23
Build-essential is not installed but Linux-headers-generic is.

---

### Post by chili555 on 2012-03-23
> **Sammel said:**
> Build-essential is not installed but Linux-headers-generic is.You'll need to get it and try again.

---

### Post by Sammel on 2012-03-23
Ok, how do I get it without ability to access internet from Ubuntu?

---

### Post by chili555 on 2012-03-23
I was afraid you'd ask that! You'll have to download the parts to a USB drive and transfer them to your Ubuntu computer and install them from here: [http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)

Be sure to match your architecture, 32-bit or 64-bit and get build-essential, dpkg-dev, g++, libc6-dev and make. Place the .deb files on your desktop and install with:```
cd Desktop
sudo dpkg -i *.deb
```Then try to compile again.

---

### Post by Sammel on 2012-03-23
I tried but got errors:

Dpkg-dev wont complete because it's dependant on Xz-utils which I don't have installed.

G++-4.4 wont complete because "Package g++-4.4 is not installed."

Build-essential wont complete because I don't have G++ installed.

Make and Lib6 installed without errors.

---

### Post by chili555 on 2012-03-23
I suggest you go back and get the dependencies, too: [http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)

Simply search for whatever is missing, grab it and install it. It may take a few tries but you'll get it.

---

### Post by Sammel on 2012-03-24
I got most of them installed but one problem remains:

I cannot install g++ because libstdc++6-4.4 is not yet defined.
But I cannot install libstdc because I dont have g++ installed.

---

### Post by chili555 on 2012-03-24
Have you downloaded libstdc++6-4.4? Can you try to install them both at the same time?```
sudo dpkg -i g++.whatevertheversionis.deb libstdc++6-4.4.whatevertheversionis.deb 
```Of course, substitute the actual version information here.

---

### Post by Sammel on 2012-03-24
Installing them both same time worked. Now I have all those packages installed.

But original problem when I try to install drivers is still same.
When try to use autorun.sh I still get the same errors.

---

### Post by chili555 on 2012-03-24
This error?> This translates to: "No rule to produce target korjaus/r81... Stop"Or some other?

---

### Post by Sammel on 2012-03-24
> **chili555 said:**
> This error?Or some other?

Yes, same lines as before:

> make[2]: *** Kohteen "korjaus/r8168-8.028.00/src" tuottamiseen ei ole sääntöä. Seis. (This translates to: "No rule to produce target korjaus/r81... Stop"
make[1]: *** [clean] Virhe 2 (This means: Error 2)
make: *** [clean] Virhe 2

---

### Post by chili555 on 2012-03-24
Are you in the correct directory? If you do:```
ls
```Is Makefile listed? Are you root?```
sudo su
```

---

### Post by Sammel on 2012-03-24
> **chili555 said:**
> Are you in the correct directory? If you do:```
ls
```Is Makefile listed? Are you root?```
sudo su
```


Thank you, using sudo su solved it.
Earlier I had used sudo <command> instead.

--
Internet connection works now without problems.

---

### Post by chili555 on 2012-03-24
Excellent! Glad it's working! Would you please use thread tools at the top and Mark Solved?

---

