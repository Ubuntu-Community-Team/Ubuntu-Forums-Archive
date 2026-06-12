---
title: "Input won't change"
date: 2010-01-12
forum: Mythbuntu
---

### Post by sqeelurgle on 2010-01-12
I have a Leadtek dtv1000s card set up with Mythbuntu 9.10.  In the backend, there are 2 capture cards set up, one for the DVB-T tuner part, and one for the analog capture part (composite and S-Video in).  In the input section, there are 3 inputs set up - Antenna, Compsite and S-video.  That all seems to me to be fine.  When I go to the frontend, and am watching live TV, I press the C key to change inputs from the antenna to an analog input and nothing happens.  I also tried pressing Y - in case that was the key to use in my set up.  No dice. It stays on the antenna input.  It is almost as if the frontend doesn't recognise the inputs exist.  The analog inputs are both set up with no grabber, and I didn't do a channel scan (I think it even skipped over that option and wouldn't let me do it if I wanted to).  There will be no channel info for them anyway, as the intention is to plug a VCR in there to watch and capture old tapes.  I am sure there is probably something simple that I am missing.  Any ideas where to start looking?

Thanks

---

### Post by baldydonald on 2010-01-13
Curiously, I have the same issue, this time with a Hauppauge Nova-T USB (DVB-T) dual-tuner stick. There are 2 inputs configured, each of which can record 2 different channels (off the same mux).
When input 1 starts to record, I can only watch channels on the same mux (which is a bit inconvenient), so I'd like to switch inputs and watch on the other tuner. I can only do this by recording a second channel on input 1, at which time myth switches over to input 2. On the plus side, I *can* record 4 channels concurrently!
I've tried using both Y and C to change inputs, with no effect.

---

### Post by sqeelurgle on 2010-01-18
Bumpage - cos I still haven't figured it out

---

### Post by Colonelguf on 2010-01-19
Y or C has never worked for me, but if I hit M (for Menu) while watching, 2 of the choices are Switch Source and Switch Input. Those always work for me.

---

### Post by baldydonald on 2010-01-20
According to [http://www.gossamer-threads.com/lists/mythtv/users/342420#342420](http://www.gossamer-threads.com/lists/mythtv/users/342420#342420) we should be using NEXTCARD - I went into Setup/Edit Keys/TV Playback/NEXTCARD and set it to be various different keys including CTRL-N and ` but unfortunately neither worked for me either.
Because I am not using an IR, just a wireless keyboard/rollerball it is easy enough to just use M and switch input that way as suggested on the previous post.

---

### Post by sqeelurgle on 2010-01-21
The menu seems to work for me - sort of.  I can select a different input, and then it goes to a completely blank screen and freezes - I have to use the power button to get any response from the computer.  Guess the issue now is getting those inputs configured correctly.

---

### Post by sqeelurgle on 2010-01-28
I got it all sorted.  I had defined a channel in the channel editor for the composite input, but i didn't know that you had to then go back into the input connection page and set that channel is the default channel fr the input.  Did that and it works fine.  There is a delay which I assume is the dealy through the card.  As long as the audio lines up time-wise when I get teh cables to hook that up too I'll be happy.

---

