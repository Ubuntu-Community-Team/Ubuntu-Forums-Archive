---
title: "HowTo: Enable system sound in Ubuntu 8.10 (Intrepid)"
date: 2009-02-16
forum: Multimedia Software
---

### Post by chunchengch on 2009-02-16
I am not sure if people still have this problem or not, but I think it will be somewhat helpful for those who have the system sound problem unsolved.

The package libcanberra installed by default in Ubuntu 8.10 (Intrepid) is version 0.6 , it seems to be obsolete and causes the system sound to work ineffectively, the following three steps will solve this problem.

**[COLOR="Blue"]Step 1: Install the newer libcanberra[/COLOR]**

open /etc/apt/sources.list

[COLOR="Red"]$ sudo gedit /etc/apt/sources.list[/COLOR]

add the following lines at the bottom

[COLOR="Green"]# PPA for Gert Kulyk (to fix system sound problem) 
deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main[/COLOR]

then update the repository

[COLOR="Red"]$ sudo apt-get update[/COLOR]

after that, update manager will prompt updates for libcanberra, just install all of them and reboot.

[COLOR="Blue"]**Step 2: Enable system sound**[/COLOR]

open **System** -> **Preferences** -> **Sound Effects** -> **Sound Effects** , check the '**Play alerts and sound effects**', and assign the sounds for every particular sound effects, now the system sound should work normally.

[COLOR="Blue"]**Step 3: Enable shutdown/logout sound**[/COLOR]

Although we enable the sound effects, however the logout sound is still missing, the solution is: 

open /etc/gdm/PostSession/Default

[COLOR="Red"]$ sudo gedit /etc/gdm/PostSession/Default[/COLOR]

add the following line before 'exit 0' and then save the file

[COLOR="Green"]**/usr/bin/canberra-gtk-play --id="desktop-logout"**[/COLOR]

now, you could hear the shutdown/logout sound when you shutdown/logout Ubuntu, enjoy it!

---

### Post by Jaques on 2009-02-17
Hi chunchengch,

thank you - works fine!

---

### Post by dndrich on 2009-03-22
OK, I did all this and the logout sound now works.  But I assigned a wave file that I know works well to the empty the trash, and still no sound on that event.  Any idea what the story is here?

---

### Post by vonhessler on 2009-04-22
Hi Ch. Thank you very much for your advice. However, I found a problem: If I activate the sound by System/Preferences/Sound, it does not work; If activate by System/Administration/Initial Window, the sound works, but block all sound applications (totem, amarok, dragon, etc). Any suggestion? (My pc is a Compaq Presario F500 Desktop)

Regards,

VONHESSLER

PS: As I run [COLOR=Red]$ sudo apt-get update, [COLOR=Black]appears the following text: [/COLOR][/COLOR][COLOR=DarkRed]W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY DBF1CA1622460E60
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/COLOR]. Help!

---

### Post by tobre on 2009-05-10
Hello
First I want to thank you for your great guide which worked perfectly for me on intrepit.
However it seem's to need some change to be used in jaunty.
So I'm asking if You could tell me how to make this work in jaunty?

tobias

---

### Post by db4elle on 2009-10-05
> PS: As I run [COLOR=Red]$ sudo apt-get update, [COLOR=Black]appears the following text: [/COLOR][/COLOR][COLOR=DarkRed]W: Error de GPG: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY DBF1CA1622460E60
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/COLOR]. Help!

you need to add the PPA's authentication key. 

Here is the [link]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xDBF1CA1622460E60") to the key you need. Copy the text portion (exclude the bold title though) into a text file and save it as 'gert-kulyk-ppa.key' for example. 

Then go to System->Software Sources->Authentication (tab)->Import key

select the file you just created and click OK. Then run update again, and you won't get the error.

Hope that helps.

---

### Post by CLEARviewF on 2010-04-22
> **chunchengch said:**
> 
[COLOR="Blue"]**Step 3: Enable shutdown/logout sound**[/COLOR]

Although we enable the sound effects, however the logout sound is still missing, the solution is: 

open /etc/gdm/PostSession/Default

[COLOR="Red"]$ sudo gedit /etc/gdm/PostSession/Default[/COLOR]

add the following line before 'exit 0' and then save the file

[COLOR="Green"]**/usr/bin/canberra-gtk-play --id="desktop-logout"**[/COLOR]

now, you could hear the shutdown/logout sound when you shutdown/logout Ubuntu, enjoy it!

Hi chunchengch,

Now we are in 2010, and Ubuntu Karmic is playing.
I can listen all the system sounds "out of the box" and edit them to my likes, but nothing about Logout sound.
What I want to know is If this "Step 3" still works for Karmic, because I still have not Logout sound "out of the box" and I would want to test this "Step 3".
Also, I am asking myself why there are so many years and Ubuntu have not solved this issue. Did not they care about this issue?
I am in Ubuntu since Edgy, and I have never listened this  god damned Logout sound :D

thank you!!

---

