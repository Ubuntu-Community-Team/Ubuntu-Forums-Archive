---
title: "Ubuntu 8.10 disabled my WindowsXP networK?"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by jesse85 on 2009-05-03
I installed 8.10 on an existing WinXP system as a dual boot option. Everything seemed fine but now my internet connection under Windows seems damaged. I don't really understand how that could happen. The network/internet connection works fine under Ubuntu. Boot into Win and it says a cable is loose. and I can't connect at all or repair it.

I'd be really surprised if Ubuntu did anything to my Windows settings but I don't have another explaination. It might have disabled my network card in Win? It's a real pain.

Is there any way to uninstall Ubuntu? Or rather reverse its effect on my Win hardware on bootup? Thanks

---

### Post by tad1073 on 2009-05-03
Seems to me that it changes things in the card its self. I had similar issues so I decided to completely remove ubuntu.

---

### Post by aikiwolfie on 2009-05-03
Changes things in the card? Are you saying Ubuntu is flashing the firmware in peoples network cards without asking them? Highly doubtful.

To the OP. Borked network connections are a known issue in Windows XP and it has nothing to do with Ubuntu. Try flushing the DNS cache.

```
ipconfig /flushdns
```

---

### Post by tad1073 on 2009-05-03
Who knows? It seems that every time I use 9.04 I have problems connecting when I boot back into Vista.

---

### Post by jesse85 on 2009-05-04
Thanks for all the suggestions. Still no joy. Strangely, at least once I booted into WinXP and it was recognizing the modem/router yesterday. I don't think I did anything in particular to make it happen. Since then, no internet connection in WinXP but it works fine in Ubuntu. I'm wondering if it was a mistake to update to Jaunty (9.04, I think)

It's really frustrating because WinXP says there's a missing cable or is unable to recognize the LAN. Info on the hardware says it is disabled/disconnected. Then I'll boot into ubuntu and it works like a charm. The only difference in my system is the installation of ubuntu so I have to think it did *something* to the WinXP settings. I just have no idea what. As far as I can tell the only thing it changed was the initial boot file and that was only to provide the dual-boot pause and menu of OS choices.

Still welcoming any bright ideas. It doesn't help that I'm not familiar with the system tools for Linux. I want to look more closely at the network connection that's working under Linux so I can see what the difference is with the WinXP situation.

---

### Post by aikiwolfie on 2009-05-05
Are you using a proper stand alone version of Ubuntu hosted on it's own partition or are you using the Wubi version intended for test driving Ubuntu?

---

### Post by jesse85 on 2009-05-05
Pretty sure it's Wubi I installed. I've also found that Ubuntu inserted a line for Windows in "boot.ini" modifies how it processes subsequent lines. It then adds a prefix all the lines of the next boot file as it processes them. I don't have a copy here (I'm having to boot back and forth between the systems to post here) but it looks like it's specifies the partition for finding all the driver files. I'll post it after I go back and get it.

My real question at this point is how to go back to the original state of my boot files. I like linux but I can't just abandon my Win programs all at once and the booting back and forth is a pain. I mean, online access is a pretty basic part of my computer work. Not being able to go online in Windows isn't an option.

Suggestions?

---

### Post by aikiwolfie on 2009-05-05
Wubi modifies the Windows boot process. So far as I know the file system is a virtual one, contained in a file rather than a partition. Basically I think Wubi is more of a VM for trialling Ubuntu running on top of or within Windows. It's certainly not without it's own set of issues.

You might find the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide") more helpful.

---

### Post by Spider7 on 2009-05-05
> **jesse85 said:**
> Thanks for all the suggestions. Still no joy. Strangely, at least once I booted into WinXP and it was recognizing the modem/router yesterday. I don't think I did anything in particular to make it happen. Since then, no internet connection in WinXP but it works fine in Ubuntu. I'm wondering if it was a mistake to update to Jaunty (9.04, I think)

It's really frustrating because WinXP says there's a missing cable or is unable to recognize the LAN. Info on the hardware says it is disabled/disconnected. Then I'll boot into ubuntu and it works like a charm. The only difference in my system is the installation of ubuntu so I have to think it did *something* to the WinXP settings. I just have no idea what. As far as I can tell the only thing it changed was the initial boot file and that was only to provide the dual-boot pause and menu of OS choices.

Still welcoming any bright ideas. It doesn't help that I'm not familiar with the system tools for Linux. I want to look more closely at the network connection that's working under Linux so I can see what the difference is with the WinXP situation.

Sounds like the problem is with the link state - DNS won't come into play until link is up. One scenario I can see is Ubuntu initialized NIC into some state the XP does not know how to recover - even though I would expect XP to reset the chips on its way up, but with all the wake-up on LAN stuff, it may not, who knows.

I would try power down ubuntu (maybe even unplug the power cord), and then boot into XP, at least to confirm the theory.

---

### Post by lance hinds on 2009-05-05
I have the same problem. older dell cmp. dual boot. lose network connection in windows after booting ubuntu. unplugging the system restores the net connection on windows...

---

### Post by aikiwolfie on 2009-05-08
Could I suggest that you guys uninstall Wubi completely to see if your Windows XP network starts working again? If it does and your happy dual booting then it might be an idea to install a proper copy of Ubuntu on it's own partition instead of running Wubi inside Windows XP.

---

### Post by cariboo on 2009-05-08
It would help a lot if you could tell us nic you are running. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

BTW you can access your windows partition from Ubuntu, no need to reboot to check files. Open Places-->Home Folder, and you should see your windows partiton in the left hand pane.

---

### Post by lance hinds on 2009-05-08
Sorry, in my case it is a fresh install of ubutu 9.04, not 8.10. The computer is a dell dimension 2350 with a broadcom bmc 440 nic.

---

### Post by aikiwolfie on 2009-05-09
> **lance hinds said:**
> Sorry, in my case it is a fresh install of ubutu 9.04, not 8.10. The computer is a dell dimension 2350 with a broadcom bmc 440 nic.

Are using Wubi like the others?

---

### Post by lance hinds on 2009-05-10
No, standard install.

---

### Post by lance hinds on 2009-05-10
And the same thing happens when I run Ubuntu in the Live CD mode.....

---

### Post by aikiwolfie on 2009-05-11
Really? That is odd. The Live CD isn't supposed to make any changes to your system at all. Have you tried flushing the DNS cache in XP with the command I posted before?

Try running the following command.

```
ipconfig /renew
```

---

### Post by lance hinds on 2009-05-12
> **aikiwolfie said:**
> Really? That is odd. The Live CD isn't supposed to make any changes to your system at all. Have you tried flushing the DNS cache in XP with the command I posted before?

Try running the following command.

```
ipconfig /renew
```


Tried this and the message returned was "No operation can be performed on local area connection while it has it's media disconnected"

---

### Post by aikiwolfie on 2009-05-13
Okay after a bit of digging around I found [this: http://www.techsupportforum.com/networking-forum/protocols-routing/220641-solved-media-disconnected-message-ipconfig.html]("http://www.techsupportforum.com/networking-forum/protocols-routing/220641-solved-media-disconnected-message-ipconfig.html"). It would seem to be worth a try.

TCP/IP stack repair options for use with Windows XP with SP2.

[list=1]
[*]Start, Run, CMD to open a command prompt:


[*]Reset TCP/IP stack to installation defaults.
```
netsh int ip reset reset.log
```


[*]Reset WINSOCK entries to installation defaults:
```
netsh winsock reset catalog
```


[*]Reboot the machine.[/list]

---

### Post by aikiwolfie on 2009-05-13
You can also try:
```
ipconfig /release {press enter}
ipconfig /renew {press enter}

```

---

### Post by lance hinds on 2009-05-14
netsh int ip reset reset.log
Made no difference.





netsh winsock reset catalog
ipconfig /release {press enter}
ipconfig /renew {press enter}Resulted in:

"No operation can be performed on local area connection while it has it's media disconnected"

---

### Post by aikiwolfie on 2009-05-16
Okay I'm out of ideas.  Sorry I can't help any further guys.

---

### Post by lance hinds on 2009-05-16
Thanks for your help. Ive submitted a bug report.

---

