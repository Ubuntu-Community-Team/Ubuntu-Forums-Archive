---
title: "[SOLVED] what to do so i can play my mp3's and all my DVD's that i PAID for"
date: 2008-09-28
forum: Multimedia Software
---

### Post by cowboyup6983 on 2008-09-28
sounds really messed up that after installing Ubuntu 8.04 it wouldnt just let me play my files. can someone show me any easy way for both.. i have newest version of ubuntu. thanks in advance for the help.

---

### Post by chalewa on 2008-09-28
someone can correct me if i am wrong, but to my understanding, you cannot. 

i assume you are talking about itunes stuff?

---

### Post by howefield on 2008-09-28
You just need to install the correct codecs. I was reading a nice sticky on this this morning, I'll try and find it.

This one

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by cowboyup6983 on 2008-09-28
> **chalewa said:**
> someone can correct me if i am wrong, but to my understanding, you cannot. 

i assume you are talking about itunes stuff?

not itnues.....mp3s

---

### Post by cariboo on 2008-09-28
Have to install Ubuntu-restricted-extras to get some of the codess you need to play your videos. Some of the codecs are illegal in some countries so they are not installed by default, You also need libdvdcss2 from the Medibuntu repositories,   again the lib isn't installed by default because it is illegal to use it in some countries.

That being said to install the ubuntu-restricted-extras you can use Add/Remove Programs, Synaptic Package Manager, and of course the command line to install them. THe first thing to do is to go to SYstem-->Administration-->Software Sources and make sure you have all the repositories enabled. Then in a Applications-->Accessories-->Terminal (only because it is easier to explain) type:

```
sudo apt-get update
```

You will be asked for a password, use the password you created during the installation of Ubuntu. Note: the password will not be echo back to you. Next in the same terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install about 60 packages, including Flash, jave and mscorefonts. The next thing to do is to go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow the instructions to enable the Medibuntu repositories for your version of Ubuntu. When you have done that. In a terminal type:

```
sudo apt-get install libdvdcss2
```

This will install the decrypter that will allow you to play DVD's

You should now be able to play most types of audio and video files.

Jim

---

### Post by cowboyup6983 on 2008-09-28
> **cariboo907 said:**
> Have to install Ubuntu-restricted-extras to get some of the codess you need to play your videos. Some of the codecs are illegal in some countries so they are not installed by default, You also need libdvdcss2 from the Medibuntu repositories,   again the lib isn't installed by default because it is illegal to use it in some countries.

That being said to install the ubuntu-restricted-extras you can use Add/Remove Programs, Synaptic Package Manager, and of course the command line to install them. THe first thing to do is to go to SYstem-->Administration-->Software Sources and make sure you have all the repositories enabled. Then in a Applications-->Accessories-->Terminal (only because it is easier to explain) type:

```
sudo apt-get update
```

You will be asked for a password, use the password you created during the installation of Ubuntu. Note: the password will not be echo back to you. Next in the same terminal type:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install about 60 packages, including Flash, jave and mscorefonts. The next thing to do is to go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow the instructions to enable the Medibuntu repositories for your version of Ubuntu. When you have done that. In a terminal type:

```
sudo apt-get install libdvdcss2
```

This will install the decrypter that will allow you to play DVD's

You should now be able to play most types of audio and video files.

Jim


right after i did this in the terminal, it went ahead and download stuff and then one popup came up and i hit enter, second one which i attached in a image below does let me hit ok or anything at the bottom. i dont know how to say yes or enter, it doesnt let me go ahead with installation. please help!!! thanks

---

### Post by howefield on 2008-09-28
use the tab key to highlight the OK button and then press enter.

---

### Post by cowboyup6983 on 2008-09-28
> **howefield said:**
> use the tab key to highlight the OK button and then press enter.

thank you!!!

---

### Post by sdybruce on 2008-09-28
I tried and it said Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

what should i do?
thanks

---

### Post by cowboyup6983 on 2008-09-28
> **sdybruce said:**
> I tried and it said Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

what should i do?
thanks

did u follow the above steps. i did and everything worked except for when i had to hit tab to press enter when it was installing the big package of stuff... weird, that it worked for me and not u. 

hey does anyone know how to play mki files on ubuntu. which program should i use.

---

### Post by Amarsingh0793 on 2008-09-28
Install ubuntu-restricted-extras (via synaptic). That includes everything you need (codecs, flash, Java e.t.c.). I recommend VLC Media Player - it plays everything :).

---

### Post by cowboyup6983 on 2008-09-28
> **Amarsingh0793 said:**
> Install ubuntu-restricted-extras (via synaptic). That includes everything you need (codecs, flash, Java e.t.c.). I recommend VLC Media Player - it plays everything :).

kwel, yes i installed VLC media player and got the mkv file to play just fine.. thanks again to all that help, im going to mark this thread as solved!!!!

---

