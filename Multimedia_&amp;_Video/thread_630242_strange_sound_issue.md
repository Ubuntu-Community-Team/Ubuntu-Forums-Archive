---
title: "strange sound issue"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by rksk16it on 2007-12-03
Hello

I am here having something which is really strange with my sound. Its not that i cant hear any sound, i can play music, play games and do all the stuff with sound but there is one strange thing..

When i start the computer there is no sound on the login screen and furthuremore **only that user can hear sound which has login first**. Eg:- if i go in as root first then only root will hear sound, no matter how many times i logout of root and login to other users...and yes i dont mean "switching users"..i mean completely logging out. If i need sound on other user i need to restart my PC.

And if i start "sound preferences" from the first user and click on "Test" button under "Devices" tab (there are four "test" buttons there , 3 for sound playback one for recording). Since i dont have mic so the fourth one is useless. So on clicking the test button i hear the test sound, but only on the **first user who logged in**, not any other user. If i click the same button from other users who logged in after the first user logged out then i get the following error message :-

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused


I have installed ALSA stuff (drivers and utils) and pulse audio server, if this helps.

I would be glad if u guys got any idea why this is happening. There are many posts regarding sound problems, but most of them deals with problems regarding no sound at all, but in my case the first user dont face any trouble.

Furthur, if the first user again logins...it will again hear the sound..as if the first user kindda "grabbed" the device in some way !!

---

### Post by rksk16it on 2007-12-03
I guess i partially solved the problem for now, but its not a complete solution, i am posting my experience just in case any1 know something about this.

Now i can hear sound on all users, no matter whoever login first, and this is what it is supposed to be.

but...

i disabled all those fancy system sounds at login screen and all those sounds that play on login and logout on ALL users (i am root, i logged in each of them and disabled that)

i completely removed everything related to pulse-audio using synaptic manager.

So, no more system sounds but atleast i can play games and listen to music :)

This all started when i installed gutsy, everything worked fine with feisty. Also since i installed gutsy there are many other problems that appeared out of nowhere, like :-

1. When i insert my USB, do data transfers and then if i "unmount" it doesnt show any message that it is safe to remove.

2. Very often during startup, shutting down or even on relogging to other user, sometimes the black screen (terminal) appears showing lots of error messages all saying something like that "device mapping failed", i dont know what it means.

I dunno what induced so many bugs in gutsy, and i am also not sure where the fault lies my hardware/kernel/gutsy/or some other piece of software. All i know that it all started after the installation of gutsy.

I would appreciate if some1 can post some info on this. In the end...good luck with gutsy and have a nice day :)

---

### Post by macabro22 on 2007-12-04
I had EXACTLY the same experience. Tryied to installl pulseaudio and JACK and got screwed. Then Removed everything and got audio back again but not when simultaneously using different apps

---

### Post by wavesound on 2008-01-30
Hi All
I to have this problem.
Pulse audio seems broke.
I can get sound from VLC ok but Totem has no sound ( nothing new there then!)
If I set the pulse audio in prefs I get:

gconfaudiosink: Failed to connect: Connection refused

So where do I go from here?

This is without the grief with youtube thats works now and again.

It seems someone took there eye of the ball with Gutsy, it's the most unstable system since Redhat 8
I'm really considering going back to 6lts.

I note they have a studio Ubuntu, you'd think they would have sound sorted, do they talk to each other?

Cheers
Bob

---

### Post by macabro22 on 2008-01-30
> **wavesound said:**
> Hi All
I to have this problem.
Pulse audio seems broke.
I can get sound from VLC ok but Totem has no sound ( nothing new there then!)
If I set the pulse audio in prefs I get:

gconfaudiosink: Failed to connect: Connection refused

So where do I go from here?

This is without the grief with youtube thats works now and again.

It seems someone took there eye of the ball with Gutsy, it's the most unstable system since Redhat 8
I'm really considering going back to 6lts.

I note they have a studio Ubuntu, you'd think they would have sound sorted, do they talk to each other?

Cheers
Bob

My experience with ubuntu studio and the realtime kernel was bad. I lost the module that loaded my ati proprietary drivers and could not recompile with that kernel.

Maybe It works with nVidia cards. I think I will give it a shot on my new Dell pc, then I will tell you how it went.

---

### Post by wavesound on 2008-01-30
Hi
 I have an Nvidia  card and it works well on this machine.
One of the things they have right.
I have set my RME multi as default card and VLC and Amorak are fine with it, but Totem refuses to play sound. Must be a g streamer thing.

Hopefully Pulse audio may improve things.

Cheers
Bob

---

