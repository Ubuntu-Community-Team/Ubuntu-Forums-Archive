---
title: "Mythbuntu running really slow"
date: 2010-05-10
forum: Mythbuntu
---

### Post by justifier on 2010-05-10
HI all,

My mythbuntu box is running really slowly, painfully slowly in fact. It has  a intel P4 3.0Ghz HT in it, so the processor shouldn't be a problem

RAM wise it has 487MB (according to information centre)

TV card is an Hauppage Nova-T-500 

i have a 320Gb internal drive with thust the OS on it and an external 1tb hard drive with all the media on it 

I presume that the ram is an issue and i have plans for upgrading that soon but should it be running this slow even with that little ram or is it definatly a ram issue. It quite often take a minuie for a menu to change and it often opens up tv says please wait then closes back to the menu.

So, any ideas please or is it just ram?

---

### Post by tgm4883 on 2010-05-10
> **justifier said:**
> HI all,

My mythbuntu box is running really slowly, painfully slowly in fact. It has  a intel P4 3.0Ghz HT in it, so the processor shouldn't be a problem

RAM wise it has 487MB (according to information centre)

TV card is an Hauppage Nova-T-500 

i have a 320Gb internal drive with thust the OS on it and an external 1tb hard drive with all the media on it 

I presume that the ram is an issue and i have plans for upgrading that soon but should it be running this slow even with that little ram or is it definatly a ram issue. It quite often take a minuie for a menu to change and it often opens up tv says please wait then closes back to the menu.

So, any ideas please or is it just ram?

Probably a ram issue. Is it still slow after you restart the frontend?

---

### Post by ghostborg on 2010-05-10
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step]("http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")

---

### Post by tgm4883 on 2010-05-10
> **ghostborg said:**
> [http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step]("http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")

How is this productive in helping the OP?

---

### Post by colinnwn on 2010-05-10
> **justifier said:**
> HI all,

My mythbuntu box is running really slowly, painfully slowly in fact. 

but should it be running this slow even with that little ram or is it definatly a ram issue. It quite often take a minuie for a menu to change and it often opens up tv says please wait then closes back to the menu.

So, any ideas please or is it just ram?

I'm not so sure it is a RAM issue. I've got 2 gigs and the equivalent of a C2D 2.9ghz processor. I have similar problems after upgrading from 9.10 to 10.04. TOP shows somewhat elevated RAM and processor usage than what I was used to, but not so high that the machine should be such a dog. Even things unrelated to Myth (like Firefox) are painfully slow now. And the hard drive is **always churning**, whereas it used to only churn when it was recording something, or I was using the computer/Myth.

Disabling EIT scan relieved about half the problem. I don't know what the remainder of the problem is. I'm about to blow away my install and hope a fresh 10.04 install won't display this behavior.

Good luck.

---

### Post by pauna on 2010-05-11
> **justifier said:**
> HI all,
My mythbuntu box is running really slowly, painfully slowly in fact. It has  a intel P4 3.0Ghz HT in it, so the processor shouldn't be a problem

RAM wise it has 487MB (according to information centre)


I have 512megs in my mythbuntu box and see no major slowness. Sure it isn't the snappiest box around, but normal operations (menu selections, DVD playback, standard TV operations) are fast enough that I don't notice the speed.

Mythbuntu 10.04 with mythtv 0.23+fixes.

What kind of processes do you have in there running as shown by top?

---

### Post by justifier on 2010-05-11
According to TOP the top 2 processes are myth front end and back end the processor is unaffected and in the memory column they are both saying 2.5.

---

### Post by justifier on 2010-05-11
It is now opening up the TV but i am getting a cannot lock errror and the procceer use is jumping up to 25% and the momry 22.5%

---

