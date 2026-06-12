---
title: "Wireless won't work after 12.04 update"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by kmax3672 on 2012-05-02
I have a Dell Studio and a few hours ago I updated to 12.04. Now my laptop won't pick up any of the wireless connections. I tried this but it didn't work

 kevin@kevin-Studio-1558:~$ dmesg | grep iwl
kevin@kevin-Studio-1558:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
kevin@kevin-Studio-1558:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13671  0 
dcdbas                 14098  1 dell_laptop
wmi                    18744  1 dell_wmi
kevin@kevin-Studio-1558:~$ sudo modprobe -r dell-wmi
kevin@kevin-Studio-1558:~$ sudo rfkill unblock all

---

### Post by TBABill on 2012-05-02
Looks like the hard blocked ( a mechanical or soft-key switch) is the issue. rfkill unblock all will only remove the soft blocked. Do you have a way to turn the wireless on/off via switch or key combination? ALT+F2, for example...could be any combo.

---

### Post by kmax3672 on 2012-05-02
I have a button actually on my F2 that is meant for turning on and off wireless. I tried that and alt F2 but neither worked

---

### Post by kmax3672 on 2012-05-02
Also,  when I go to system setting and then Network there is no wireless network, and I don't know how to create a wireless network.

---

### Post by TBABill on 2012-05-03
I'm not sure you can while it is hard blocked.

---

### Post by TBABill on 2012-05-03
Have you tried other key combinations than the one you already know for turning wireless on in Windows? It's possible Ubuntu thinks you need, via the dell_wmi, that the combination is actually something else. Try ALT+ different function keys to see if any enable the wireless. Could just be a key mapping error rather than a hardware problem.

---

### Post by AdrianP on 2012-05-03
You might want to try post #2 of this thread [http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096) which has just worked for me (see post #6 there for a description of the problem I had)

---

### Post by chanhteo on 2013-02-25
sudo rmmod -f dell-laptop sudo rfkill unblock all 

This works for me !

---

