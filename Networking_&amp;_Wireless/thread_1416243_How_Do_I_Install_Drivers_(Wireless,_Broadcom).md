---
title: "How Do I Install Drivers? (Wireless, Broadcom)"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by Code N on 2010-02-25
I'm probably going to sound retarded but I don't know how to install drivers. I just installed Ubuntu today. I'm pretty good with following directions but this is my first time using Ubuntu, so go easy on me. 



PS: I installed it because Vista basically died on me, and I don't have the recovery discs. Please Help!

---

### Post by Revolutionary101 on 2010-02-25
Get the driver from the manufacturers website and then follow this tutorial.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you have any questions just ask.

Lastly, welcome to Ubuntu. I hope you enjoy it.

---

### Post by wojox on 2010-02-25
What does this say ? Run it in the terminal:

```
lspci | grep -i net
```

---

### Post by oldsoundguy on 2010-02-25
In most cases, you don't have to install any drivers.  Unless you have a Fred Flintstone wireless or sound card set up. (Broadcom = Fred Flintstone)
You can install the restricted drivers for video to tweak it, (available in the restricted drivers repository) but most other hardware will now install out of the box. (Wacom is an issue, but they are co-operating with Linux, so help is available for their pads.)

Unlike Windows, where you have to go all over the web to the manufacturer's sites to get the latest drivers.

---

### Post by Code N on 2010-02-25
lspci | grep -i net```
code@CODE:~$ lspci | grep -i net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
code@CODE:~$ 

```And to the guy that tried to link me to a tutorial, the link didn't work.


> **oldsoundguy said:**
> You can install the restricted drivers for video to tweak it, (available in the restricted drivers repository)
  Ah, but how do I get there and install it?

---

### Post by Revolutionary101 on 2010-02-25
Here is the fixed link

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by theozzlives on 2010-02-25
> **Code N said:**
> lspci | grep -i net```
code@CODE:~$ lspci | grep -i net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
code@CODE:~$ 

```
And to the guy that tried to link me to a tutorial, the link didn't work.

Go to System > Administration > Hardware Drivers and activate your driver (wired connection).

---

### Post by wojox on 2010-02-25
[Installing drivers for the BCM]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20drivers%20for%20the%20BCM4311,4312,4321,4322%20Cards")

---

### Post by Code N on 2010-02-25
> **theozzlives said:**
> Go to System > Administration > Hardware Drivers and activate your driver (wired connection).

I don't have any drivers listed. ;)

*Currently following Wojox advice* What's the "Restricted repository"?

---

### Post by ndefontenay on 2010-02-25
I agree. You shouldn't need to use an ndiswrapper. only enabling your restricted driver should work.

Note I've had 2 options one of which didn't work and my install totally failed to boot after installing 2nd option.

After re-installing and choosing option 2 everything worked fine.

Keep trying :)

---

### Post by bkratz on 2010-02-25
See this thread he/she has the same card

[http://ubuntuforums.org/showthread.php?t=1412627](http://ubuntuforums.org/showthread.php?t=1412627)

---

### Post by theozzlives on 2010-02-25
In System > Administration > Software Sources

---

### Post by Code N on 2010-02-25
I typed this into the terminal and...
```
code@CODE:~$ ~$ sudo apt-get update && sudo apt-get install bcmwl-kernel-source
~$: command not found
code@CODE:~$ 


```

---

### Post by wojox on 2010-02-25
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source

```

---

### Post by Code N on 2010-02-25
> **wojox said:**
> ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source

```

I can't type the password for some reason. It stays blank.

---

### Post by ndefontenay on 2010-02-25
Hi.

On terminal password doesn't show even * it stays blank but it's there. Just try pressing enter.

It should work fine.

---

### Post by Code N on 2010-02-25
> **ndefontenay said:**
> Hi.

On terminal password doesn't show even * it stays blank but it's there. Just try pressing enter.

It should work fine.
Wow, I fail.

Thanks if this works! Wojux, this guy, and everybody else who tried to help me. Do you guys memorize these commands?

---

### Post by Code N on 2010-02-25
OMG! It worked, I can see my drivers! OMG! You guys are amazing! Hopefully I'll continue to learn stuff, and not give up like most people. First time I used Ubuntu.

---

