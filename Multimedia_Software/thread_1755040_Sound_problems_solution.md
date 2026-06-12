---
title: "Sound problems solution?"
date: 2011-05-10
forum: Multimedia Software
---

### Post by spur on 2011-05-10
I have noticed a few threads on getting sound to work properly. I had a problem getting my internal sound card to work on 5.1 channels and investigated the links and information given in the various threads and found that there are slight differences from the references to what I had to do.
 Firstly, it's a good idea to read through these links first.
 _[Ubuntu Surround Sound]("https://help.ubuntu.com/community/SurroundSound")_  
 _[How to surround sound Hardy]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/")_
 Then:-
 
[LIST=1]
[*]Check to see if the sound is     working and save the terminal output for later use.  Code     “speaker-test -Dplug:surround51 -c6 -l1 -twav” for 5.1 test.
[*]Open the conf file for editing.     Code “gksu gedit /etc/pulse/daemon.conf” or as I needed “sudo     kate/etc/pulse/daemon.conf”  (Kubuntu 11:04)
[*]Change the line **;     default-sample-channels = 2****     to (default-sample-channels =6). No parenthesis and no ; mark.**
[*]The nest line on my system was for     channel configuration, but is absent on the examples given in the     links. Uncomment the line by removing the ; mark and then taking the     saved output from the terminal add in so the order is the same the     channels. I made sure I called every thing the same as well. My rear     centre channel was labelled CFE so I used that for the edit. Double     check spelling and punctuation. A comma was needed between each     channel for my system.
[*]Save and exit the lot then reboot.     I found that after reboot Kmix gave me all the options I needed and     I had access to surround sound. Beautiful!
[/LIST]

---

### Post by ratcheer on 2011-05-11
I have followed your instructions.

When I run "aplay Front_Left.wav", the pavumeter shows all channels active, which is puzzling. Shouldn't it just be the front left channel?

But, when I run "speaker-test -Dplug:surround51 -c6 -l1 -twav", nothing on pavumeter is active.

In no cases am I getting any output to my speakers.

Thanks,
Tim

---

### Post by spur on 2011-05-11
If you are getting no sound when you run the code to test the speakers, then something isn't right with the Alsa config or install, as that is the side of the action it's testing. I would consider uninstalling Alsa then reinstalling it. First I would try a software update to be sure you had the latest version. Personally, as I'm a bit over careful at times, I would uninstall the Pulse Audio and reinstallthat after reinstall Alsa. No reason just my feeling that as pulse depends on Alsa I'd get that working then reinstall Pulse and let it dtect (if it will) Alsa. 
Be aware I'm not an Ubuntu expert just someone who has  'fiddled' around with it for a few years now. I am quite prepared for any one else who is an expert to jump in and correct me, I'll learn that way :) .

---

### Post by ratcheer on 2011-05-11
Well, it sure couldn't hurt.

Thanks,
Tim

---

