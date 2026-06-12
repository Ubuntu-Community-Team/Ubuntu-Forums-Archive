---
title: "Get Controller Working"
date: 2020-07-05
forum: MINT
---

### Post by threecharecterusername on 2020-07-05
i posted this in the mint forums, but since its been 5 and a half hours, there are 13 users online there and mint is basically just green Ubuntu, i now call upon what i hope is a larger and more active forum so i can just get on with my life. also, i am going to be smarter and list the os im using as mint 18.3

[COLOR=#333333][FONT=&quot]i have a controller, a Wii U pro controller connected to my PC using a Magic NS adapter, and i want to use it in my Linux VM. i currently do not have it working, and i want to know the steps i have to go through in order to get it working.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]i have tried it in both x and d input modes.


[/FONT][/COLOR]

---

### Post by wildmanne39 on 2020-07-05
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by threecharecterusername on 2020-07-05
wow. i didnt even know there was a mint page. huh.

---

### Post by threecharecterusername on 2020-07-05
now the real question is is there anyone that uses it.

cause there are like 3 people that use mint in the entire world and im two and a half of them.

edit, at 1048 GMT, the current population of the mint forums is me and 9 guests.

---

### Post by deadflowr on 2020-07-05
Might work with xwiimote.
Though I'm not sure what the magic ns adapter is or whether that is linux compatible.
But the wii u pro controller should or at least could work through normal bluetooth.

See here on xwiimote: [https://dvdhrm.github.io/xwiimote/]("https://dvdhrm.github.io/xwiimote/")
Check if your's is one of the supported devices.

Also double check that the VM has access to the adapter,
but that probably depends on which type of VM is used.
(types of VMS could be VMWare, Virtualbox, qemu-kvm, or even xen or perhaps parallels, among others)


Edit: Forgot to add that xwiimote and xserver-xorg-input-xwiimote packages are already in the Ubuntu archives (So also available on mint),
though they tend be older versions.

---

### Post by threecharecterusername on 2020-07-06
thanks. ill check this one. and the magic NS connects to the wii u controller and makes the computer think its just a normal xbox kinda type controller. not exactly an xbox, but similar.

---

### Post by Holger_Gehrke on 2020-07-06
If that Magic NS adapter you're using is a supported Bluetooth receiver / transmitter, then the Wii U Pro Controller should get seen as a HID-device and be supported without any further trouble. Two years ago somebody [posted an article]("https://cubiclenate.com/2018/04/15/wii-u-pro-controller-on-opensuse-linux/") about getting it to work with openSUSE and expressed regret about how easy it was because he had hoped to get a longer and more interesting article out of it ... If it was that easy on openSUSE back then, it should be just as easy on other Linux-systems now.

Holger

---

### Post by threecharecterusername on 2020-07-06
i am going to call this fixed, since it pointed me in the right direction, and now i have to get back to the forums of the game i am trying to play and see what they have to say, since now the issue is with the game and not just the os.

---

