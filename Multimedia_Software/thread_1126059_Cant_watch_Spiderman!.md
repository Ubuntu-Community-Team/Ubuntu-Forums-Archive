---
title: "Cant watch Spiderman!"
date: 2009-04-15
forum: Multimedia Software
---

### Post by rreyes1316 on 2009-04-15
Hello all.

I'm a newbie here--approximately 3 days old to be exact.

I am trying to watch--and closely match my setting as close as possible to Windows as possible--a movie and test my dvd rom settings. I want to make sure I can copy/backup music and dvd's, burn, including iso's, and listen to and watch movies. Amongst this list I am trying to solve is the movie viewing. From what I have read there is something about CSS--ok, I understand. But then there is the libdvdread 4 thingy that I must execute via the terminal . . .um,ok. So I go there, insert the first command then get prompted for a password--what the heck! I don't know it. I frustratingly try and try but to no avail and no sooner than later give up. The only thing staring back at me is that damn blinking cursor that has refused to take my keyboard input. When I have installed other programs I was prompted for a password to allow it permission. This was the password I used in the initial setup--You would think this was the same password that was requested from me at the terminal--but it was not. But then again, when I typed in the PW it would not display in the terminal.

In anycase, how the heck can I rip, burn, copy, extract, view, edit dvd's--mostly concerned with viewing as the first step--so that I can make backup copy's of them? I swear . . .nothing is more irritating than a parent with a young boy that leaves my movies strewn about the table plunged with fingerprints and scratches.

Well . . .I hope you can help in a "This Is How It's Done for Dummies" format that is easy for me to understand at my old age.

much thanks

---

### Post by leonardo_neo on 2009-04-15
Ok, you have put so many things, difficult to answer all of them. I will try to help you out with them one by one if possible.

So first thing first. Have you installed the media codecs yet? These codecs will help you to watch and real almost any type of media available for general use. To install these codecs you need to install medibuntu repository. Read the link below to enable medibuntu repository. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

From this repository you need to install these two codecs.

1. libdvdcss2
2. w32codecs

In case you have some difficulty to install these packages, then do let us know. 

After you install these packages, you should install the restricted extras package. Open terminal and type this command....

> sudo apt-get install ubuntu-restricted-extras 

When you enter the password, ***it doesn't show anything on the page***!! So don't think that there is something wrong with the Ubuntu OS, or your keyboard. Just type your password and hit enter, it will do it's job :D

Let's first deal with your 'viewing' media problem. Burning, copying, ripping can be dealt afterwards. 

:)

---

### Post by ibuclaw on 2009-04-15
We have a Comprehensive Multimedia and Video HowTo sticky at the top of this forum. Which includes both video codecs and DVD playback.

Be sure to review the page first
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Regards
Iain

---

### Post by rreyes1316 on 2009-04-15
The packafe installer says it is already installed. I went to the add/remove app and all I found was 3 ubunt, kubuntu, and xubuntu related files to libdvdcss2. I have the downloading Package files window with a progress bar but not much progress has occured. I was trying to install some thing els late last night, went to bed, and woke up with the same progress bar with no progress. I rebooted the pc and started the recommended steps mentioned above and here I am.

---

### Post by rreyes1316 on 2009-04-15
Tinivole. Ah . . .but talking to people is so much more fun. I love meeting new folks. But I will certainly read that this evening. 

Hope to chat further

Thanks

---

### Post by Swagman on 2009-04-15
Worked for me.

Thanks very muchly

---

### Post by Sylslay on 2009-04-15
I had install Juanty 9,04 beta, than I install that

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

and since than , evry meida file working perfect.

---

### Post by rreyes1316 on 2009-04-15
Ok. I have done Sylseys tip and it worked--sort of. There was a lot of activity on the terminal but I cannot watch the dvd yet. Then I tried the :

1. libdvdcss2
2. w32codecs

Ubuntu restricted extras already installed. Should I install the kubuntu and xubuntu as well? There were no matching apps for w32codecs.BTW, is the repository another name for Add/Remove App?

---

### Post by Peasantoid on 2009-04-15
The repository is where packages are stored. Add/Remove Applications is just one of the many ways of accessing it.

You may have better luck finding these packages with Synaptic (System > Administration > Synaptic Package Manager).

---

### Post by rreyes1316 on 2009-04-15
THanks. I have just closed all windows and tried synaptic. I get a window that says "Another Synaptic is Running". I only have my web browser open.

---

### Post by Peasantoid on 2009-04-15
Are you running apt-get? Is someone *else* running apt-get, perhaps in a different account?

---

### Post by rreyes1316 on 2009-04-15
Hmm? I don't even know what thatis and how I might have started it. I rebooted and it does the same thing. Would ithace been better of I had installed the 32bit instead? How about the last stable version instead? If so, how do I remove this one and replace with stable version?

---

### Post by rreyes1316 on 2009-04-15
OK. I rebooted and opened synaptic but it would not respond. Then there was an icon on the upper right corner that said system crash. Tried to launch syn but does not work.

---

### Post by rreyes1316 on 2009-04-16
BUMP!?

I reinstalled everything including XP. This time I created a partition on the hard drive for Ubuntu. Not sure what happened the first time around. When I was prompted to install on whole disk, largest empty space, or side by side, I chose the latter. This time I chose the largest--lets see if this helps.

Before anything else, I did the update and extras download via the terminal. I hope this works.

On a side note, I also tried to install 8.10 but it would not display on my Dell 30" Ultra Sharp monitor. Not so sharp after all, I guess. Any idea on this?

BTW, I installed the 64bit ver. Let me know if you guys are still following this.

Thanks:)

---

### Post by rreyes1316 on 2009-04-16
Hooray!! I got it working. Sitting at home with my spine relaxed watching spiderman; however, when I put the disc in the previews played then there was some lag and picture stuttering. After a few reboots, thinking that might help, I skipped the previews, managed to get to the dvd play buton and start the movie. I have an 8800 GTS 512 video card. I believe I have installed the nvidia drivers when I went to system>preferences>Appearance and set up the visual effects. Are there others I should have included?

Also, I installed the "w64codecs" figuring that this is the one I needed for this 9.04 amd64 install.

---

