---
title: "Getting close! Problems with 950Q."
date: 2010-05-22
forum: Mythbuntu
---

### Post by anti_microsoft on 2010-05-22
Hello all,

Yesterday I downloaded Mythbuntu 10.04 to give it a try (failed really bad in the past).

I have 2 tuners and I have one hooked up, the Happauge 950Q. I was impressed to get a result. I ran through the net looking for ideas to get the tuner to work. I got a picture :D.

Now, the problem is that I do indeed have a picture. The picture is stacked with one duplicate on top of the other. I made the local.conf file and was able to get a signal. I also changed all the resolutions under the recording areas to 720x480. 

The other problem I have is no sound. I decided to download tvtime and give it a try and make sure all is well, good sound and video there.

Is there a way to solve this? Feel I am getting close. I also have a Pinnacle 800i if that may be easier to setup?

Thanks in advance for the help!

---

### Post by ian dobson on 2010-05-22
Hi,

What graphic card are you using? The double picture problem could come from an ATI graphic card.

I've never had much luck with Pinnacle cards, Happauge have a better name in the Linux community.

Regards
Ian Dobson

---

### Post by anti_microsoft on 2010-05-22
Thanks for the ATI info!

I googled and found out howto fix that issue, you were correct.. ATI card.

I also somehow got audio to work. Tried using /dev/dsp2 as the card audio and it never worked, tried again and all the sudden it works.

So got sound,picture and a pretty much happy camper :D.

I now need to figure out how to get that CC data off the top of the screen. Been trying different things but it stays.

---

### Post by ian dobson on 2010-05-22
Hi,

Sorry, but what do you mean by "CC data"?

Regards
Ian Dobson

---

### Post by anti_microsoft on 2010-05-22
Closed Caption data that creates a ever changing line at the top :D.

---

