---
title: "Install Celestia on 32-bit Xenial"
date: 2016-07-18
forum: Multimedia Software
---

### Post by SciGuy1872 on 2016-07-18
Hi.  I think Celestia is a great program and I found these instructions on AskUbuntu for Celestia and Xenial:  [http://askubuntu.com/questions/780596/install-celestia-on-ubuntu-16-04#comment1168994_780599](http://askubuntu.com/questions/780596/install-celestia-on-ubuntu-16-04#comment1168994_780599)


Is it even wise to put Celestia on 16.04, should I just consider the program a casualty of time?  This sentence is what one user wtote:
> [COLOR=#111111][FONT=Ubuntu]Notice that celestia depends on several packages that are known for break backwards compatibility (libgtk) and this version can cause problems on the foreseeable future[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[U][B][I]
The post:[/I][/B][/U]
The answer provided by dadexix86 works and if you want to check the checksums of the packages for security (since the packages aren't being installed by apt, their integrity is not automatically checked (I think)), it's probably best to do everything manually.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However, for a simple copy-paste solution, the following bash commands should do the job (assuming you have a 64-bit, standard, fresh Ubuntu 16.04 installation):[/FONT][/COLOR]
UBUNTU_MIRROR=https://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/c/celestia

# common
sudo apt-get install liblua5.1-0
wget "${UBUNTU_MIRROR}"/celestia-common_1.6.1+dfsg-3.1_all.deb
sudo dpkg -i celestia-common_1.6.1+dfsg-3.1_all.deb
sudo apt-get install celestia-common-nonfree

# for celestia-glut
wget "${UBUNTU_MIRROR}"/celestia-glut_1.6.1+dfsg-3.1_amd64.deb
sudo apt-get install freeglut3
sudo dpkg -i celestia-glut_1.6.1+dfsg-3.1_amd64.deb

# for celestia-gnome
wget "${UBUNTU_MIRROR}"/celestia-gnome_1.6.1+dfsg-3.1_amd64.deb
sudo apt-get install libgtkglext1 libgnome2-0 libgnomeui-0
sudo dpkg -i celestia-gnome_1.6.1+dfsg-3.1_amd64.deb
[COLOR=#111111][FONT=Ubuntu]This includes the dependencies (installed using apt from Xenial) and celestia-common-nonfree (also installed from Xenial).
[U][I][B]End Post.

[/B][/I][/U]For the wget lines, should i enter the " and the $ or should I just go right into the address?

If it is okay to put Celestia on Xenial, should I just replace the amd64.deb with i386.deb?   In the post, the address of Celestia is given and the poster writes that the user can just download it there--I couldn't find a way to make the program run.

Thanks,
    Anthony[/FONT][/COLOR]

---

### Post by SciGuy1872 on 2016-07-25
Does anyone have any thoughts about what putting Celestia on Xenial would do to my computer, per this comment from a poster?  
      
> [COLOR=#111111][FONT=Ubuntu]*Notice that celestia depends on several packages that are known for break backwards compatibility (libgtk) and this version can cause problems on the foreseeable future*[/FONT][/COLOR]

Things are wonderful and I don't want to take a chance--Celestia was great on Precise, but I can let it go, if needs be.
Thanks,
   Anthony

---

### Post by &amp;KyT$0P# on 2016-07-25
> Celestia was great on Precise
So can you just run Ubuntu 12.04 in a virtual machine and run Celestia in that Ubuntu 12.04?

I personally have only ever uses [VirtualBox]("https://www.virtualbox.org/") for virtualization, but you might prefer QEMU/KVM (which is also free, and it's available from the standard Ubuntu package repositories).

---

### Post by SciGuy1872 on 2016-07-25
Thanks for the reply.  Will put QEMU/KVM on Xenial--I haven't had to use virtualization before, so thanks for the tip.
Thanks,
     Anthony

---

### Post by &amp;KyT$0P# on 2016-07-25
You're welcome.

I had previously looked into installing QEMU/KVM and discovered that finding information about it is not so easy, so to get you started, here are a couple links:
[https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")
[https://www.howtoforge.com/tutorial/kvm-on-ubuntu-14.04/]("https://www.howtoforge.com/tutorial/kvm-on-ubuntu-14.04/")

Don't think I can help more than that, sorry.  If you need more help there is of course the Virtualisation forum here [https://ubuntuforums.org/forumdisplay.php?f=308](https://ubuntuforums.org/forumdisplay.php?f=308)

---

