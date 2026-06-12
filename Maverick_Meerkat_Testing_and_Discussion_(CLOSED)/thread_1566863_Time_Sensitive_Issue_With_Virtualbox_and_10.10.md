---
title: "Time Sensitive Issue With Virtualbox and 10.10"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by techunit on 2010-09-02
Hi this is Techunit from ubuntuvideotutorials.org, and we need to start working on the Basics series for ubuntu 10.10 but when we attempt to install the virtualbox guest editions we encounter a problem with Xorg. I know this is a documented issue in the virtualbox forums, but they had no solutions. As an experienced Ubuntu user I attempted to force version of Xorg to the lucid version to see if that would work. I know that the problem is with a unsupported version of Xorg. Which package would be the one to try? Is there a way to install xorg or its components via a ppa or some other method, I am hoping that Oracle will have an update for Virtualbox soon before the RC but we need to get to work. Many thanks Techunit

---

### Post by cariboo on 2010-09-03
It's a virtual box problem, they have to update the guest additions to work with Xorg 1.9.

---

### Post by techunit on 2010-09-03
But isn't there a way I could get it to work be reverting to an old Xorg version? I got a little farther by doing it but I wasn't able to go anywhere, I just got a fixed size that was bigger.

---

### Post by cariboo on 2010-09-03
The only thing I can suggest is to try kvm, that may have the necessary changes.

---

### Post by techunit on 2010-09-03
KVM? well its worth a short. I really need to have these videos out quickly. Purhaps I can find a beta version of Virtualbox that supports the Xorg?

---

### Post by techunit on 2010-09-03
Well I futzed with that one. It appears while kvm may support xorg it doesn't support the kind of acceleration and vertualization that I need to produce the videos. I guess untill the update comes out we will have low res tutorials for the basics series. Not that bad but hardly 720p

---

### Post by xebian on 2010-09-03
I read somewhere that you can try the VBox from the repo which may have a guest addition hacked for X 1.9.  I didn't try it though.

For some reasons VB 3.2.8 guest installer has a check for X1.9 not to install.

---

### Post by techunit on 2010-09-03
Which repo? Meerkat? I tryed to download that from the repository in the vm but I can't find the .iso, it isn't in the normal place I would expect to find it. I looked in the home directory but nothing

---

### Post by cariboo on 2010-09-03
Have you tried installing maverick on a spare partition, then installing vbox and the additions from the repositories?

---

### Post by techunit on 2010-09-03
Ok I know how to fix the problem... What you need to do is install the old xorg drivers. To do this you will have to open the sources list.

```
sudo gedit /etc/apt/sources.list
```

then put pound symbols infront of the maverick main restricted lines (4 of them)

Ok then open the software sources app and add the lucid main restricted
```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
```

Ok now reload the packages and make sure that everything is working with apt. 

Now go to the synaptic package manager and go to "status" click installed and enter "xorg" into the quick search option then go to xorg-server-core (something like that (second entery after xorg) and mark it for removal (now everything with xorg in its name should be set to be removed) apply and reboot.

Now when you reboot you will see a command line interface. Log-in and type

```
sudo apt-get install xorg
```

now the old xorg drivers from lucid are running! next install the Virtualbox Guest Editions (you may see and error goblygook message) if you see the screen crazy error then wait 3 minutes and hit enter on the keyboard. Then click close on the vm and check send shutdown signal and hit enter. after that you should have access to changing the settings and screen freely!

---

### Post by xebian on 2010-09-03
> **techunit said:**
> Which repo? Meerkat? I tryed to download that from the repository in the vm but I can't find the .iso, it isn't in the normal place I would expect to find it. I looked in the home directory but nothing

why are you looking for .iso?  Look for these
```

i   virtualbox-3.2                                   - Oracle VM VirtualBox                                       
p   virtualbox-guest-additions                       - guest additions iso image for VirtualBox                   
p   virtualbox-ose                                   - x86 virtualization solution - base binaries                
p   virtualbox-ose-dbg                               - x86 virtualization solution - debugging symbols            
p   virtualbox-ose-dkms                              - x86 virtualization solution - kernel module sources for dkm
p   virtualbox-ose-fuse                              - x86 virtualization solution - virtual filesystem           
p   virtualbox-ose-guest-dkms                        - x86 virtualization solution - guest addition module source 
p   virtualbox-ose-guest-utils                       - x86 virtualization solution - non-X11 guest utilities      
p   virtualbox-ose-guest-x11                         - x86 virtualization solution - X11 guest utilities          
p   virtualbox-ose-qt                                - x86 virtualization solution - Qt based user interface    
```

and then install the particular package

---

### Post by cariboo on 2010-09-03
If you're running Maverick with Xorg from Lucid, than you aren't really running Maverick, it's more like a Frankenstein's monster. :) So you won't be giving your readers a true look at Maverick.

---

### Post by xebian on 2010-09-03
> **cariboo907 said:**
> If you're running Maverick with Xorg from Lucid, than you aren't really running Maverick, it's more like a Frankenstein's monster. :) So you won't be giving your readers a true look at Maverick.

Don't be ridiculous.  It's just as maverick as yours with a downgraded Xorg version.

---

### Post by ktp on 2010-09-03
> **xebian said:**
> Don't be ridiculous.  It's just as maverick as yours with a downgraded Xorg version.

it is but it isn't right...some thing might not work just right.

---

