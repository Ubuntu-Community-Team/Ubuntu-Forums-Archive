---
title: "Ardour/Firepod Issue"
date: 2007-08-19
forum: Multimedia Production
---

### Post by Thelonius on 2007-08-19
I recently started using Ubuntu Studio, and I bought a Presonus Firepod so I could record with Ardour. I read everything I could find on how to properly set up my machine to work with the firepod, and I'm pretty sure its connected and working. It shows up in the hardware manager, and JACK has been configured correctly and appears to be working fine.

However, Ardour doesn't seem to be picking up any sound when I run a direct line in from a keyboard to the firepod - I hear the instrument out of the headphone jack on the firepod, but when I try to play the track back, no sound follows. The same happens when trying to record a mic'd instrument. Maybe I just don't know the program well enough, or is there something I'm forgetting to do? Any help is greatly appreciated.

---

### Post by duffrecords on 2007-08-21
Did you arm the track for recording?

---

### Post by Thelonius on 2007-08-21
Yes, if that means selecting the little record icon on the track itself.

---

### Post by kayosiii on 2007-08-21
Are you jacking audio out of the keyboard or midi?
You can't reccord midi in Ardour directly yet (scheduled for next release AFAIK). Unless you are specifically using Audio cables out of the keyboard it is almost certainly going to a midi connection. 

If you are jacking audio you have to make sure that the track you are recording to is the connected to the right input - the best tool for this I have found is called patchage.

If you are recording midi then you will need to patch either 

a) patch the midi input for the firepod into a softsynth (I like zynaddsubfx or amsynth) and then patch the audio output of that into ardour if you want to get an audio track.

Or

b) Use something like Rosegarden to record the midi data directly and run it synced to ardour.

---

### Post by Thelonius on 2007-08-22
I know I am jacking audio out of the keyboard; I never use midi. So I need to patch the correct input on the firepod to the equivalent track in Ardour? How might I go about doing that?

---

### Post by nalmeth on 2007-08-22
I've attached a screenshot of jack connections when ardour is open with a session. Generally the connections are pretty self-explanatory and you should be able to surmise how it works.

One thing I'd like to point out, on the Firepod, next to the mic jack there is a mixer knob.

The knob should be all the way LEFT on INPUTS rather than on PLAYBACK

If none of this helps please post your jack connections and your jack settings

---

### Post by Thelonius on 2007-08-22
Maybe I've found a problem... the only two things connected with a line in my patchbay are Ardour 01 and Freebob_pcm, whereas you seem to have many more. Do I need to manually connect all the inputs and outputs under these headings?

---

### Post by Thelonius on 2007-08-22
Here are my Jack settings as well, if they are needed.

---

### Post by nalmeth on 2007-08-22
Looks like this is just a routing problem

In Ardour, add a new track, and jack SHOULD automatically route: 
freebob-pcm = dev1-linein 1+2 left ---> Ardour = Audio 1/in 1

For whatever reason, the audio signal doesn't appear in the mixer until you start recording. SO:

Arm the track, and start recording. Your audio data should show on the region, and you should see activity in the meter (shift-e to make it appear)

EDIT!! My instructions are for using the connections window, not the patchbay, I didn't realize this until just now. Perhaps your setup with the patchbay has caused some problems.
Can you post what your connections window looks like?

---

### Post by Thelonius on 2007-08-22
Here is my connections window when Ardour is open:

---

### Post by nalmeth on 2007-08-22
Ok.. so what happens when you add a track? Does jack automatically route the connections for you?

---

### Post by Thelonius on 2007-08-22
It appears too... when I added a track, a line was added connecting dev1c_ Input 3L to Audio 2/in 1.

Also, since I've started checking the connections window, I've been getting xruns constantly, whereas before I hadn't been getting any. Is this unrelated?

Ignore the first thumbnail.

---

### Post by Thelonius on 2007-08-22
Here is the correct one.

---

### Post by nalmeth on 2007-08-22
I'm not sure about the xruns, I don't think that just having the connections window open should cause anything, but do the xruns stop when you close it?

From your screenshot, it looks like the 3rd input on your firepod was connected to the 2nd track.
If your keyboard is hooked up to another input, you'll have to either switch it to input 3, or change the jack connection.

If everything IS hooked up right, and you can't get ardour to record anything, there must be a problem with the mixer settings on your firepod, or a problem with Ardour

I'll take a look at the thread tomorrow

---

