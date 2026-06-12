---
title: "Skype / Music Player Conflict"
date: 2009-03-02
forum: Multimedia Software
---

### Post by scoobymad555 on 2009-03-02
Hey peeps,

Running the following ....

Hardy 8.04 patched / updated according to update manager
Using Gnome desktop environment
Alsa
Skype Client 2.0.0.72
Amarok 1.4.9.1 (using kde 3.5.10)


Seems to be some kind of hardware ownership/control clash between amarok and skype client. The skype client runs happily but when i have amarok playing and get an incoming call it's not able to use or take ownership of the audio device so as i answer the call it actually diverts it to the voicemail service instead. If i try to make an outbound call i get an "audio hardware fault" message. 

The work-around i have at the moment is stopping playback manually before making an outbound call and forcing the skype client to trigger a command ("killall amarokapp") for incoming coming calls. 

It's a niggly gripe but it's basically annoying to have to keep hitting stop before making a call or having to re-open the music player after receiving a call. Plus, using killall to terminate the app does seem a little brutal lol! I did find some documentation on controlling amarok from command line with a google search but it was based on gentoo build running kde and I basically had no success in getting the commands to work despite altering syntax to what i guessed it should be.

(i'd prefer not to change music player/manager if i can help it)

Any ideas / suggestions?

Cheers :)

---

### Post by scoobymad555 on 2009-03-02
some more googling .....

the dcop command! :D

syntax : "dcop amarok player stop" .... well it's better than killall :)

just gotta figure out a way to tie it into skype now so it does it for me ;)

---

### Post by scoobymad555 on 2009-03-02
ok so still fiddling with this to get it right ...

currently have the skype client initiating one of two scripts depending on what i need now with pretty good results ....

script 1 : "amarokstop.sh"

#!/bin/bash

dcop amarok player pause
dcop amarok player stop

(it stops playback instantly this way rather than fading the volume out when just using the stop option on its own)


script 2 : "amarokplay.sh"

#!/bin/bash

sleep 10
dcop amarok player play

(gives enough time for skype to release the hardware. Without the sleep command amarok tries to start instantly but crashes)


This is working perfectly for the incoming calls by configuring actions in the "notifications" tab within skype but i can't get it to initiate properly for outgoing calls. I've tried applying the appropriate script to the "outgoing call ringing" and "call connecting" notifications but they're not actioning early enough. Ideally I need to apply it on a Call Initiation Action but I can't find this anywhere. I'm assuming it doesn't exist so i'll have to live with manually pausing / stopping it myself before making a call for the time being .... unless someone can suggest something? :)

---

