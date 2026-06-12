---
title: "Adobe Air (Iplayer) on 64 bit"
date: 2009-09-23
forum: Mythbuntu
---

### Post by timswait on 2009-09-23
I'm trying to get BBC Iplayer to work for downloaded programs. This means I have to install Adobe Air. The problem is I'm running a 64 bit system, and Air's only available for 32. I've followed the instructions on [http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04]("http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04"), but have got stuck. The command to install:
```
$ ./AdobeAIRInstaller.bin
```
gives me the error message:
```
bash: ./AdobeAIRInstaller.bin: Permission denied
```
What does this mean, I'm not that familiar with Linux? Where exactly do I need to save the AdobeAIRInstaller.bin file to on my computer? I have put it in my home directory, is this correct?
Cheers

---

### Post by tgm4883 on 2009-09-23
> **timswait said:**
> I'm trying to get BBC Iplayer to work for downloaded programs. This means I have to install Adobe Air. The problem is I'm running a 64 bit system, and Air's only available for 32. I've followed the instructions on [http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04]("http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04"), but have got stuck. The command to install:
```
$ ./AdobeAIRInstaller.bin
```
gives me the error message:
```
bash: ./AdobeAIRInstaller.bin: Permission denied
```
What does this mean, I'm not that familiar with Linux? Where exactly do I need to save the AdobeAIRInstaller.bin file to on my computer? I have put it in my home directory, is this correct?
Cheers

You need to use sudo

```
sudo ./AdobeAIRInstaller.bin
```

---

### Post by timswait on 2009-09-24
Thanks for the suggestion, but I'd already tried it, I get:
```
sudo: ./AdobeAIRInstaller.bin: command not found
```
Is it that I've not saved the .bin file in the wrong place? Where does it need to go?
Cheers

---

### Post by SiHa on 2009-09-24
The **./** means look in the current directory, so you need to be in the same directory that AdobeAIRInstaller.bin is saved.

You say it's in your home directory, so you could type ```
sudo ~/AdobeAIRInstaller.bin
``` ('~' is the shortcut for your home directory.)

Also you probably need to make the file executable. Again assuming you are in the directory that it's saved - ```
sudo chmod a+x AdobeAIRInstaller.bin
```
Finally, Linux is case-sensitive, so you need to make sure that the filename you type matches **exactly** the name of the file as saved.

---

### Post by timswait on 2009-09-24
Thank you for that, the chmod seems to be what was needed, after I did that it installed fine, funny Adobe don't mention that step in ther documentation.
I now have another problem. I then installed IPlayer desktop without problem, and it appeared in my Applications menu, but nothing happens when I click on it. Any ideas what this problem is?

---

### Post by SiHa on 2009-09-24
Not sure, sorry not played with iPlayer on Linux.
There's a couple of posts on the BBC site that mention it trying to use 64bit libs instead of the32bit ones it needs.

---

### Post by gdbutcher on 2009-10-25
> I then installed IPlayer desktop without problem, and it appeared in my Applications menu, but nothing happens when I click on it. Any ideas what this problem is?

Timswait, did you get the Iplayer working? I think you have to do this before it works properly, copy and paste each line into your terminal one by one:

```
sudo apt-get install ia32-libs
sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1
```

then final copy and paste this line:

```
sudo cp /usr/lib/libadobecertstore.so /usr/lib32
```

worked for me, hope this helps

---

