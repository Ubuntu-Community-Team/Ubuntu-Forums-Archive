---
title: "NovaT-500, multiple recordings per tuner?"
date: 2009-05-07
forum: Mythbuntu
---

### Post by SiHa on 2009-05-07
So there's an option in the backend setup 'Number of recordings possible on this tuner'. And I've read previously of people recording more than one show at a time on a single tuner.

I've spoken to a colleague at work who is very knowledgeable about DVB matters, and he reckons that most likely, Myth is only recording the Transport Stream. This is, essentially a number of Program Streams muxed together. So it looks like it should be possible.

Does anybody use this feature on a NovaT-500?

I could try it out blind, but I'd hate for the wife to lose a recording because I'd cocked up.

[LIST]
[*]I assume that for simultaneous recordings the two shows would have to be on the same MUX?

[*]Are **all** channels on a single mux in a single TS? or are there muliple TS per MUX?

[*]Say, I had 4 simultaneous recordings scheduled (2 per tuner, Does Myth know what MUX (or TS) they are on, and will it flag a conflict if the sceduled recordings use more MUXes than Tuners?
[/LIST]

For information, I'm in the UK and receive from the Rowridge Transmitter.

Any advice greatfully received. I've got three tuners anyway, so it's rare that I need more than that, but occasionally it happens :)

---

### Post by ian dobson on 2009-05-07
Hi,

When you want to record two programs from the same tuner at the same time, the two program must be in the same transport stream from your provider. Mythtv passes the TS to the multirec code that splits the TS unto multiple PS (program streams) on per program you want to record, that are then written to the harddisk as seperate files.

Myth knows which channel is in which TS and also knows which program is on which channel so YES, if you try to record 4 programs that are on 3 different TS then myth will warn you, or try and reschedule a recording so that there are no conflicts.

Regards
Ian Dobson

---

### Post by SiHa on 2009-05-07
Nice concise answer, thank you.

So, all I need to do is change the 'Max Recordings' field to 2?

Maybe I'll have a play over the weekend when there's not much scheduled

---

### Post by ian dobson on 2009-05-07
Hi,

Yes, just start myth-setup and go to the tuners page and you set the max number of recordings per card change it to 2 and restart the myth-backend programm. Thats it.

Rgards
Ian Dobson

---

### Post by Chris Musampa on 2009-05-07
I was investigating this feature last night (briefly and not by any means exhaustively), I set both tuners for 2 recordings max each, they then show up in mythweb status page as 4 encoders.  I found that if a do 2 recordings from the same TS it still, at least sometimes, seems to use both tuners so I can't then watch another channel on a different TS.  

Is there a way to force it to pull all programmes on the same TS from the same tuner even if the other tuner is idle?  Not a big deal for me but would seem more logical and a better use of the hardware.

---

### Post by AlecJ on 2009-05-07
I have 5 DVB-T tuners, two of which are a novaT500, their all set for 1 recording. When they were set for 2 recordings I had problems watching and recording on the same tuner, with quality and signal loss, and your locked to channels on the same multiplex as the one being recorded.

If you select 2 recordings in the backend, you will have 2 extra tuners ready for use, their numbered so you can select to use them in the recording options you select when you setup a program for recording. But the channels must be on the same multiplex for this to work. i,e BBC1,2,3 are on the same multiplex but ITV and 5..etc are on others so you can't use one tunner to record BBC one and ITV at the same time.
I got fed up with this complication and turned the function off and went ebaying for more tuners instead. The USB one's work fine.

---

### Post by nickrout on 2009-05-07
> **Chris Musampa said:**
> I was investigating this feature last night (briefly and not by any means exhaustively), I set both tuners for 2 recordings max each, they then show up in mythweb status page as 4 encoders.  I found that if a do 2 recordings from the same TS it still, at least sometimes, seems to use both tuners so I can't then watch another channel on a different TS.  

Is there a way to force it to pull all programmes on the same TS from the same tuner even if the other tuner is idle?  Not a big deal for me but would seem more logical and a better use of the hardware.

Why only 2 per tuner? My dvb-s cards do 4 per tuner. dvb-t can do the same. I know people with 6 virtual channels per tuner.

---

### Post by Chris Musampa on 2009-05-07
> **nickrout said:**
> Why only 2 per tuner? My dvb-s cards do 4 per tuner. dvb-t can do the same. I know people with 6 virtual channels per tuner.

I was just interested to see if and how well it worked TBH, for the amount of tv I record/watch it will be a rarely used feature for me.

---

### Post by SiHa on 2009-05-08
Same here,

Thanks all for your input. I'll give it a try over the weekend, if it's going to cause LiveTV problems though, I might give it a miss. 

Seems to me that the Myth code could do with a tweak to be a bit more 'intelligent' when choosing which tuners to use. Even when recording a single channel per tuner, I've had to manually select different tuners for adjacent shows on the same channel otherwise it uses I lose the padding and one or other gets chopped if the timing is out.

Anyone know if there's anything planned for 0.22 in this area?

---

### Post by nickrout on 2009-05-08
if you post to the mythtv-users mailing list you'll get a good answer. There are people on there who know the scheduler backwards and inside out.

---

### Post by SiHa on 2009-05-08
Thanks, I've never quite got round to subscribing to the mailing list. Perhaps now is the time.

Cheers,

Simon

---

