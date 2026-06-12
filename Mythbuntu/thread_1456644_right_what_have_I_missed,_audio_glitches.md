---
title: "right what have I missed, audio glitches?"
date: 2010-04-17
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-04-17
I have been suffering with occasional audio"clicks"on my myth set up while watching dvb-t on both live tv and recordings since my first install.I had tried lots of aerials, cables amp head amp etc as wel as tweaking anything to do with audio I could find in myth but with no luck.

just recently the clicks have stopped so long as I am ripping dvds with handbrake in the background.in my simple brain I dont understand what is going on here but wondered if it could be some thing to do with cpu throttling maybe and handbrake load is enough to prevent throttling back? could it be anything else?

thanks

---

### Post by geekyhawkes on 2010-04-18
I can watch tv for 20-30mins without any clicking then for about 5mins or so i will get a click every 3 seconds.  

Am i the only one experiencing this?

---

### Post by geekyhawkes on 2010-04-30
So my audio is definatly better when i am ripping dvds in the background so in my simple head it can only be one of two things:

1)the CPU throttling that is applied when ripping (or not)
2)Some kind of HDD data throttling/data rate/HDD spin down when using just myth

I have no idea how i can tell which of the above it is, is there someway in a bash terminal I can see the CPU throttling in use so i can try and work out what the difference is when running handbrake and myth, then just myth by itself?

Thanks

---

### Post by My Name on 2010-04-30
The only thing I can think of is to try enabling/disabling the aggressive? audio buffer option. I think it is in options/livetv/general.

---

### Post by ian dobson on 2010-04-30
Hi,

This will show the cpu speed:-

cat /proc/cpuinfo | grep -A 6 "processor.*:.*$i" | grep "cpu MHz"

ust run it from the terminal prompt.

Regards
Ian Dobson

---

### Post by geekyhawkes on 2010-05-01
I have had a play with the audio buffering options and didnt really see much change to be honest.  THe problem is the clicking is pretty random so working out if anything makes a difference or not is tricky.  

I will look at the cpu speed as listed above and see if the cpu is throttling back too much.

---

### Post by geekyhawkes on 2010-05-02
Hmm, its not CPU throttling then, the grep report is 2600, 2600 regardless of myth or myth+handbrake.  

What else could be going on?  Is there some sort of data throttling with the HDD?

---

### Post by geekyhawkes on 2010-05-10
Right, after some sampling over time the cpu freq scaling isnt the problem.  Is there any chance its a hard drive scaling issue (if such a thing exists?)  How might i find out?

---

