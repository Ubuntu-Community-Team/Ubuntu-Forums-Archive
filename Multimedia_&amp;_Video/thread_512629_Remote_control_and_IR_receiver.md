---
title: "Remote control and IR receiver"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by bglaze1 on 2007-07-29
I have been trying to figure out how people configure their remote controls to work with their multimedia. I was going to get a Hauppauge PVR-150 capture card, but I noticed that some had a IR Receiver built in, while others (like the MCE versions) don't.  I have searched around and can't find any mention that the MCE versions come with an IR receiver.  So I am left with a few unanswered questions:

1) How would the MCE version function without having an IR receiver on the card?  
2) Does the MCE version come with an IR receiver that just isn't shown or mentioned?  
3) Do you need to get a seperate IR receiver in order for the remote to function?  
4) Do the MCE versions have an IR receiver built in with no external IR input?  
5) If not, and I needed to get a seperate IR receiver, would any one work, or are some not compatible with different remotes?

I plan to use my Hauppauge card in a MythTV system.  Which capture card would be better for my situation given that I want to use an RF remote (One for All URC-9910) that comes with an RF to IR converter so I can control my system from the other room.  Would it be best to just get a Hauppauge card with a built in IR receiver or the MCE version and then get a seperate IR receiver?  What are the pros of using an MCE card?  What are the cons?  Are they both supported the same in LIRC?  Is one easier to get up and running than the other?

Thanks in advance for your help with any of these simple questions.

---

### Post by tgm4883 on 2007-07-29
> **bglaze1 said:**
> I have been trying to figure out how people configure their remote controls to work with their multimedia. I was going to get a Hauppauge PVR-150 capture card, but I noticed that some had a IR Receiver built in, while others (like the MCE versions) don't.  I have searched around and can't find any mention that the MCE versions come with an IR receiver.  So I am left with a few unanswered questions:

1) How would the MCE version function without having an IR receiver on the card?  
2) Does the MCE version come with an IR receiver that just isn't shown or mentioned?  
3) Do you need to get a seperate IR receiver in order for the remote to function?  
4) Do the MCE versions have an IR receiver built in with no external IR input?  
5) If not, and I needed to get a seperate IR receiver, would any one work, or are some not compatible with different remotes?

I plan to use my Hauppauge card in a MythTV system.  Which capture card would be better for my situation given that I want to use an RF remote (One for All URC-9910) that comes with an RF to IR converter so I can control my system from the other room.  Would it be best to just get a Hauppauge card with a built in IR receiver or the MCE version and then get a seperate IR receiver?  What are the pros of using an MCE card?  What are the cons?  Are they both supported the same in LIRC?  Is one easier to get up and running than the other?

Thanks in advance for your help with any of these simple questions.

Ok, this is what you want to do (based on the fact you want to use your URC-9910).  You have 2 options, but first lets explain a little something about LIRC (what allows you to use a remote with your computer)

LIRC will take the commands from the remote and convert them into keyboard commands (like the M key, or the R key).  MythTV (and other programs as well) are controlled by your keyboard, and since LIRC converts the IR commands into Keys, your remote can also control these programs.

Now, as to the PVR-150 IR Receiver.  I would recommend getting (or making) a serial IR receiver.  Getting something like this will give you the biggest range of options, as you will be able to use many different remotes, and (as I found out), if you want to control your TV through IR transmitting, the PVR-150 IR receiver is unable to capture the IR signals from other remotes.  AFAIK, the best IR receiver for capturing the IR commands of other remotes is a serial IR Receiver.

If you use the PVR-150 on card receiver, then you are limited to the amount of buttons on the PVR-150 remote, AND you can only use the PVR-150 remote (you should be able to also use the URC-9910 remote, as that is a learning remote and you can learn the PVR-150 remote signals)

Either way, the PVR-150 (MCE or not) is controlled by keyboard keys (and LIRC sends keyboard keys).  So if I were to do it again, I would get the cheaper version of the two, a MCE remote (I didn't have any other remotes I like, but it sounds like you have a good remote), and a serial IR Receiver (for getting the IR commands to control my TV.

---

### Post by bglaze1 on 2007-07-29
First of all, thanks for your quick response.  That was very helpful and a nice simple explanation of LIRC.  You said:

> ... I would recommend getting (or making) a serial IR receiver. Getting something like this will give you the biggest range of options, as you will be able to use many different remotes, and (as I found out), if you want to control your TV through IR transmitting, the PVR-150 IR receiver is unable to capture the IR signals from other remotes. AFAIK, the best IR receiver for capturing the IR commands of other remotes is a serial IR Receiver.

I don't have the tools to build my own (although if I knew someone with them, I would definitely be interested in building one - I like the accomplishment of doing it on my own).  

But, since I must purchase one, can you recommend a good serial IR receiver?  
Is there much difference in serial receivers out there, or should I just get the cheapest one I can find?  
What should I be looking for to know it is a good one?
Do all serial receivers work the same?  
I like that this would then allow me the flexibility to use my remote and program different functionality into it.

Thanks again for your help.

---

### Post by hackmeister on 2007-08-02
I have the 150 card without the remote and picked up M$ MCE remote and usb IR receiver/transmitter:
[http://pdavila.homelinux.org:8080/blog/?p=229](http://pdavila.homelinux.org:8080/blog/?p=229)

I picked it up for $38 at NewEgg but just found this site that has it for $29:
[http://www.pcalchemy.com/product_info.php/pName/microsoft-mce-remote-control-for-windows-xp-mce/cName/remote-controls](http://www.pcalchemy.com/product_info.php/pName/microsoft-mce-remote-control-for-windows-xp-mce/cName/remote-controls)

I also wrote up a how-to for controlling my Motorola DCT700 cable box:
[https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script?highlight=%28dct700%29](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script?highlight=%28dct700%29)

---

