---
title: "No sound in rear speakers."
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by videocheez on 2007-06-12
I have an integrated 8 channel HD audio CODEC sigmatel 9221 which is on my Intel D975XBX mother board. I have 5.1 speaker set up and want to know how to set-up 5.1 speakers in ubuntu.

I'm using Rhythmbox 0.10.0a and with the  HDA  Intel ALSA mixer, there is no volume control or even a button for rear speaker.  I have front, LFE, side, surround and center volume controls but nothing for the rear speaker.  I'm wondering is there a differnent driver out there that could capture the full ability of my sound card.  Any help will be appreciated.

Thanks is advance,

VC

---

### Post by videocheez on 2007-06-15
Man i have been striking out with getting replys lately.

---

### Post by linuxwizard on 2007-06-15
Hi
right click on the speaker on your gnome panel >click on open volume control > edit tab > preferences > make sure you have everything checked that you want to show up on the mixer for controlling your volume. I don't have a rear speaker setting also, never noticed it before.


[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by videocheez on 2007-06-16
Thanks for the link.  It lhelped me to confirm that i cannot hear from the rear speaker.

```

speaker-test -Dplug:surround51 -c6 -l1 -twav

```


When the test was run and got to rear speakers, there was no sound heard for rear left and rear right.

---

### Post by motang on 2007-06-19
> **videocheez said:**
> Thanks for the link.  It lhelped me to confirm that i cannot hear from the rear speaker.

```

speaker-test -Dplug:surround51 -c6 -l1 -twav

```


When the test was run and got to rear speakers, there was no sound heard for rear left and rear right.

Now that you have checked marked everything in the _sound control panel_, turn up the **Wave Surround** and it should work if you heard *rear left* and *rear right* after you ran: ```

speaker-test -Dplug:surround51 -c6 -l1 -twav

```
I hope this works for you as it worked for me, good luck.

---

### Post by videocheez on 2007-06-19
Let me clarify.  When the program got to the point where it shoudl have said left rear and then right rear it **did not** say them.  
I think it must be a driver issue but I'm too much of noob to figure it out.  Anyways, I have temporarily stopped working on this and am focusing on getting Beryl to operate with my ATI graphics card.:(  Slowy, week by week I'm tryin to add functionality that worked so smootly with Windows into Ubuntu.

As soon as I get the video system dialed in the way I like, I will be addressing the audio problems so if you have any advice in the meanwhile......I'm all ears.;)

---

### Post by mgmiller on 2007-06-20
I just went through this on a recent build of Feisty for my son.  He has rear speakers that were not working.  I only had stereo speakers on my machine, so I never needed to figure it out.  Here is how to get it work and how to test it for 2 channel, 4 channel, 6 channel (5.1) and 8 channel (7.1):

To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
     (you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 


To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
```
speaker-test -Dplug:surround71 -c8 -l1 -twav
```
5.1 channel surround:
```
speaker-test -Dplug:surround51 -c6 -l1 -twav

```
4 channel surround:
 ```
speaker-test -Dplug:surround40 -c4 -l1 -twav
```

2 channel:
 ```
speaker-test -Dplug:front -c2 -l1 -twav
```

for more info:
```
man speaker-test
```

:popcorn:

---

### Post by videocheez on 2007-06-20
Thanks for looking  at my post.  I don't have a 4 or 6 channel button on the options tab.  Maybe I need to update alsa mixer.  Do you know how to do that?

---

### Post by mgmiller on 2007-06-20
> videocheez  	Thanks for looking at my post. I don't have a 4 or 6 channel button on the options tab.

Did you select the channel mode check box?
What are your choices in the options tab?  Dild you try clicking where it says 2ch?

Just as an aside, I discovered on my sons computer that after I had turned everything on, he still didn't get rear sound.  It turned out I had plugged the rear speakers into the wrong port on the motherboard.  Try moving the rear speaker jack around while the speaker test voice is playing.  If you remove the -l1 switch from the command line, it will keep playing till you close the terminal window.  It should look like this:

```
speaker-test -Dplug:surround40 -c4 -twav
```

---

### Post by videocheez on 2007-06-20
Thanks.  it's worth try but a similar speaker test while connected to windows works.

---

### Post by mgmiller on 2007-06-21
> Thanks. it's worth try but a similar speaker test while connected to windows works.

Here's the weird part.  My sons machine dual boots XP and Ubuntu.  He almost never uses windows any more.  The way I had the speakers plugged in in windows produced sound in the rear channels.  In Ubuntu it did not.  I had to move the rear speakers to a different jack to get sound.  I also found a different jack produced better sound in the front speakers in Ubuntu as well.  I really don't have an explanation for this beyond perhaps the widows driver setting up the output jacks one way and Linux driver doing it another way.  Al he cares about it that they all work in Ubuntu now.

---

### Post by videocheez on 2007-06-21
> **mgmiller said:**
> Here's the weird part.  My sons machine dual boots XP and Ubuntu.  He almost never uses windows any more.  The way I had the speakers plugged in in windows produced sound in the rear channels.  In Ubuntu it did not.  I had to move the rear speakers to a different jack to get sound.  I also found a different jack produced better sound in the front speakers in Ubuntu as well.  I really don't have an explanation for this beyond perhaps the widows driver setting up the output jacks one way and Linux driver doing it another way.  Al he cares about it that they all work in Ubuntu now.

Hmmmm.  It figures.  Tonight I will try your suggestions.  I have had two simultaneous Linux projects going on and now that the video situation is acceptable, I'm ready to get my audio dialed in.  Hopefully I too will be able to reduce my reliance on Windows like you son has.  I'm basically trying to either duplicate or improve upon all of the apps that I ran in Windows so that I no longer need Windows.

---

### Post by pt123 on 2007-06-21
Hey I had similar problems sometime back and to get it to work I had to check the the 6ch mode in the "Options" table of the volume control panel. 

If I remember correctly this option didn't show up initially until I installed alsamixergui .


Also if you want to test out if the rear works when playing mp3s - in the switches tab check "Duplicate front"

---

### Post by old_geekster on 2007-06-21
Besides checking the "Surround", I also check "Duplicate Front" in the "Switches" area.

---

### Post by zeeduv on 2007-11-09
haha, I had the surround all the way down, turned it up, still didn't work. Went back to check again and noticed it was muted....I am SUCH a noob.  Thanks for the tips guys.  I am slowly slipping away from windows.  Now I just need to get azureus working somehow and figure out what i'm going to do with my ipod/itunes library.

---

### Post by mrbiscuit on 2007-11-09
Ah, are the options for surround sound not showing up for you in the preferences too? I have the same problem, but it's not Ubuntu related, because I tried Arch Linux/SuSe (latest versions, with ALSA 1.0.14) and they also would not register that my card had surround sound capabilities, and I had SS with Feisty... I'm going to compile the latest ALSA and try that, I'll reply back if it works :)

---

### Post by rajeev1204 on 2008-03-25
i dont have sound in rear speakers either.

I tried setting 4 ch , surround etc all options.

my board has realtek alc 883 codec and i have creative inspire 4.1 4400 speakers


oooh solved it. Had to change sound card port from line in to mic ( red instead of orange - wierd but works now)

---

