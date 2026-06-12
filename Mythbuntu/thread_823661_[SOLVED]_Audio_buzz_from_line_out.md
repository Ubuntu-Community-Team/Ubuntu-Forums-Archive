---
title: "[SOLVED] Audio buzz from line out"
date: 2008-06-09
forum: Mythbuntu
---

### Post by bah1976 on 2008-06-09
I am just finishing my first be/fe load, and I am having an audio problem that i'm hoping somebody can help me with.  I'll preface this by saying I don't think it's an actual myth issue, but I don't know where else to post.  Any opinions are welcome.  
I have a Biostar TF560+ (v5.x) with integrated ALC888 audio.  I have a relatively cheap belkin cable connecting the 1/8" line out to RCA Red/White on my receiver.  Without even watching anything, I get a buzz coming out of my speakers.  I think the cable is ok, I've used it in the past to output line out from a laptop to watch torrent'd stuff.  Unfortunately, I don't have any other cables to try - I even sold my computer speakers recently so I got nuttin' else to test with.  I've got Master, PCM, and Front at 100% in alsamixer - do I maybe have something too high?  I've messed around with the levels, even muting everything, and i still get the buzz so I don't think it's a level problem.  So that leaves me either with an ALC888 problem or a cable problem.  I either have to buy a new sound card or a new cable - I'm hoping for opinions first.  I do also have in my stack of old computer parts a "Soundblaster live 5.1" and a "soundblaster PCI512".  I have an open PCI slot I could use - does anybody have any experience with these or know off hand if 8.04 supports them?

Thanks in advance for all opinions...

---

### Post by ian dobson on 2008-06-09
Hi,

If the buzz is a low frequency (50Hz) then if could be a problem with earth. Try connecting the case of the PC to the case (metal) of the receiver.

With regards the to sound card, I can't say anything. Maybe try the cards and see what happens.

Regards
Ian Dobson

---

### Post by Trollslayer on 2008-06-09
50Hz buzz usually means an earthing problem.
Silly question number one - are the plugs in properly?

---

### Post by Dilligaf on 2008-06-09
I don't know where you're located but something like this [http://www.radioshack.com/product/index.jsp?productId=2062214&cp=&sr=1&origkw=ground+isolator&kw=ground+isolator&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2062214&cp=&sr=1&origkw=ground+isolator&kw=ground+isolator&parentPage=search) will fix your ground loop buzzing.

Mike

---

### Post by bah1976 on 2008-06-10
Well I'll be darned - kudos to ian for the case-to-case test.  If I touch wire from PC case to Receiver case - no more buzz.  I suppose it makes sense - the computer is grounded, but the receiver is a generic two-prong plug.  Is that why "looping" them worked - did the receiver get grounded through the PC case?  So now here is my electricity 101 question - which would be better in the long run:
1) Connect the ground/earth screw that I found on the back of the receiver to the ground in the outlet.  Any suggestions on how to physically accomplish this?  I don't want to just poke a wire into the ground on the outlet.
2) Connect the receiver ground to the computer case.  Is there any risk to my server this way?
3) Buy the radioshack part mentioned by dilligaf

---

### Post by ian dobson on 2008-06-10
Hi,

Just run a wire from the PC case to the receiver. I wouldn't recommend playing with mans plugs.

The case of the PC should be grounded anyway. As long as nothing goes really wrong with the ground line on the PC you shouldn't have any problems.

I would recomend that you run the reciever/PC from the same mains point using a multi mains plug (I'm not sure what their called in engish) with a switch so that you can switch everything on/off. If you disconnect the PC from the mains you should make sure that the reciever is also switched off.

Regards
Ian Dobson

---

### Post by allene222 on 2008-06-10
The PC is PROBABLY properly grounded so running the wire to the RX from the PC would probably be ok.  You might also find that just turning the plug on the Rx around in the outlet, if it is not keyed, would solve your problem.  Personally, I am very careful about my grounds and at one point have a wire from a water pipe running to the ground of my TV.  I had to do that to get rid of some grounding problem.  You can also see ground problems as lines that move up slowly on your picture.  Also important to have all equipment plugged into the same circuit and using the same ground reference (same circuit should do that).

Allen

---

### Post by bah1976 on 2008-06-10
Thank you to all - problem is solved.  I connected the receiver ground to the screw that's holding the PSU in the case, and all is just as it should be.  For reference, all my AV equipment, including this myth box, are plugged into the same power strip, which is then plugged into the wall.  The only components that are grounded are the actual power strip and the computer - everything else is just two-pronged power with no ground.  So by connecting the receiver to the PC, I have successfully grounded and removed the audio buzz.

Thanks all!

---

### Post by NOLA_man on 2008-07-27
I have the same buzzing coming from my receiver, but I'm using a laptop, any suggestions? I have a mini plug about 12' into the mini/rca adapter, these are from Radio Shack, not the highest quality for cables, but still get the job done. The cable might seem a little long, my laptop sits on my coffee table networked, I love it this way...everything is a fingertip away.

Thanks for the help.
Mark:guitar:

Oh, if you're looking for a good steaming site,
try [http://www.accuradio.com/classicrock/](http://www.accuradio.com/classicrock/)
Still listen to Jime, Elvis and Janis...

---

### Post by bah1976 on 2008-07-28
I believe the cause of the buzzing to be that one of your components is grounded and the other is not.  Chances are, your receiver is not grounded since all but the highest end models are a simple two-pronged plug, , and the laptop is grounded.  I can think of a couple ways to try it - get one of those three-prong/two-prong adapters, that you can plug a grounded plug into, and then it would plug into an old non-grounded outlet.  Use that on your laptop to 'remove' the ground.  That may help.  If not, then try the radio shack ground loop isolator part mentioned above.

---

