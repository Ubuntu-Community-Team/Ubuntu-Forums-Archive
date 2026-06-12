---
title: "Soundcard not recognised?"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Chymera on 2007-07-27
[[IMG]http://img503.imageshack.us/img503/6553/screenshot5mz9.th.png[/IMG]](http://img503.imageshack.us/my.php?image=screenshot5mz9.png)

as you can see my soundcard is being recognised by ubuntu. It is however a 5.1 model, which alsa seems not to detect (showing only 2 channels). I have mentioned 5.1 support as being flawed on the discussion board for gutsy gibbon. Yet i was told 5.1 support works very well already.... or at least for others it does... do any of you ave an idea how i could work a  way around this problem?

---

### Post by kyphi on 2007-07-28
To identify your sound devices type the following into a terminal:

```
# aplay -l
```

I don't understand your problem.  Can you give me more information as to what you want to achieve, please.

---

### Post by nzadLithium on 2007-07-28
I think what is wanted is the surround sound options. I have these in my volume control. You click the options tab to find them. You don't have them though. To get them i think you need to goto edit preferences (in the sound control) and add Surround Jack Mode and Channel Mode
I'm not quite sure what surround jack mode is but channel mode is what you want to setup how many speakers you have. 
And my surround jack mode is set to independent.
Also i think if you want to have surround sound you need to force detection in whatever audio programs you are  using.

And i find it useful to also add duplicate front. Then while i know i am listening to 2.0 sound i activate that (on the switches tab that will appear once you add it) it will use 5.1 sound for that as well. I'm not sure what having duplicate front does to things that are already playing in 5.1 though so i always disable when listening to surround sound movies etc.

---

### Post by Chymera on 2007-07-28
Well if you couldnt understand my first post.....  My sound card has 6 channels (5.1 model), and, according to the alsa website it IS supported, however, i get only 2 channels for volume control (stereo), corresponding to only 4 speakers.

tried both your sugestions

[[IMG]http://img184.imageshack.us/img184/3465/screenshot6ka5.th.png[/IMG]](http://img184.imageshack.us/my.php?image=screenshot6ka5.png)

channel mode refers in my case to "four channel mode", whereas i need 6, and even if i enable the option from the menu aswell as from the 2nd tab, i still get only 2 channels in volume control

---

### Post by nzadLithium on 2007-07-28
When you say channel mode in your case refers to 4 channels does that mean it currently says 4 channels? or that is the maximum it lets you have?

If it currently says 4 channels try clicking it and changing it to 6

If it only says you can have a maximum of 4 channels then it is possible ubuntu is using the wrong sound driver. Or the sound driver is not setup properly Or that your sound card doesn't actually do 5.1.

Surround controls back left and right volumes. I'm not sure what controls only front. Center contols center speakers and im not sure what controls subwoofer. (these should all be able to be added from edit preferences)

If none of this helps can you please post who made your soundcard and what model it is? Then i can see if you need to do anything to get it going.

also if you find out what controls only front then can u post here? my front sound is alot louder than my back at mo. :(

---

### Post by Chymera on 2007-07-28
If i go through the trouble of uploading a screenshot at least click the thumbnail will you?
by 4 channels i mean that its the only additional option containing the word "channels" i see in my preferences. You cannot change from 4 to 6 channels, because there is no option for that.
If i said my sound card is 5.1 it probably is 5.1
My soundcard model can be seen in each of the screenshots, if you would be kind enough to go through the trouble of clicking it. 
 

The fact is that even if i click "4 channels" i still get only 2 volume control bars.

---

### Post by deadgobby on 2007-07-28
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
 all so double click on the speaker icon and go to the switches tab and make sure IEC958 is unchecked.
 You may want to install alsamixergui and play with the settings.
Gobby

---

### Post by Chymera on 2007-07-28
if you too would have made the immense effort of clicking the screenshots i posted you might have seen that i already have alsamixergui. 10x for the link though, its kind of weird, ive tried the commands to test if i have 5.1 sound, and to my great surprise, it actually worked, it recognised the center speaker, and all the rest of them.... only the sound from my rear left speaker was heavily disturbed, even though when listening to music it works just fine (except 4-speaker-stereo-mode, of course)

---

### Post by deadgobby on 2007-07-28
YOU do not need to be snippy to people on trying to help you out. THIS is ALSA mxier GUI!!!! So the next time you need help. Be nice or be one your own.
Gobby

---

### Post by nzadLithium on 2007-07-28
If you want extra volume controls then like i said before you need to add them using edit preferences.

---

### Post by Chymera on 2007-07-28
I cant, there is no 6-channel mode under edit>pref

---

