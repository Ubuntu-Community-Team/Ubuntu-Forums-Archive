---
title: "Jack Does not show Line in connections, only two capture connection which is mic"
date: 2010-09-30
forum: Multimedia Software
---

### Post by pramodbutte on 2010-09-30
I have a Turtle beach TBS-3300 DDL sound card. I am outputting the sound to a 2.1 speaker system and I have connected my guitar effect processor (GT-8, stereo) to the line in (blue) jack. I am currently using Ubuntu 10.10 (maverick), but had exactly same problem with the previous version (lucid)

When Jack is not running I can get sound from the line in. After I start Jack server, I cannot see the "Line-in" in the connection window, neither does 'line-in' stop working (I can still hear the sound, which means even if jack is running alsa is routing the sound to the speakers).

I cannot record my guitar with ardor or any other jack enabled application by routing the "line-in" to these applications.

Does any one know how to make jack detect all the inputs such as mic and line-in in order to route the sound. I am hoping to figure out a way to see "stereo line-in" inputs which I will be able to route.

I appreciate any help, thank you

---

### Post by cchhrriiss121212 on 2010-09-30
I take it jack is running OK, no error messages in the message window?
You say that jack shows up 2 capture connections, I'd bet that one of them is your line-in and one is your mic-in, connect them up to find out which is which.

---

### Post by pramodbutte on 2010-09-30
Yes Jack is running with no error messages. 

Neither of those two connections is a "line-in". I tested the connections and they are mic-ins.
In fact, the line-in sound should have stopped working once the jack server is up because there are no connections to the speakers.

---

### Post by cchhrriiss121212 on 2010-09-30
So you have 2 inputs showing up in jack, how many inputs do you have on your PC?

---

### Post by pramodbutte on 2010-09-30
I have three inputs

1. Line in (stereo)
2. Mic in (stereo)
3. S/PDIF Digital In

I have attached the pic showing all the connections

---

### Post by cchhrriiss121212 on 2010-09-30
> I tested the connections and they are mic-ins.
So what does this mean? You seem to have only one mic-in.
> 
In fact, the line-in sound should have stopped working once the jack  server is up because there are no connections to the speakers.
This is also odd, do you just hear anything that is plugged into your line-in without running any applications?

---

### Post by pramodbutte on 2010-09-30
> 
[QUOTE]I tested the connections and they are mic-ins.
So what does this mean? You seem to have only one mic-in.[/QUOTE]

When I connect either capture1/2 to the speaker, I do not get any sound from my guitar (which is connected to line in), but from the mic connection.

I have attached the screen-shots:
1. screenshot1: not input on line in, capture not connected to the speakers. strangely the meterbridge shows saturated signal.

> [QUOTE]In fact, the line-in sound should have stopped working once the jack server is up because there are no connections to the speakers.
This is also odd, do you just hear anything that is plugged into your line-in without running any applications?[/QUOTE]

When there is not connection to the speakers (in Jack) I can still hear the guitar, even when I am not running any other app.

screenshot2: No connections to any output (line out active), but I can still hear my guitar playing.

Additionally, line-in is expected to show up as a stereo input(left/right).

---

### Post by cchhrriiss121212 on 2010-10-01
This could be something to do with your pulse settings. Try looking in preferences>sound and experimenting with the input settings.

---

### Post by pramodbutte on 2010-10-01
Thanks for your input. This is what I have found so far,

1. In Maverick, pulse is not killed when jack server is started.

2. In the jack preferences, you have to specifically choose the input from line-in (Jack connections is not showing line-in and mic-in simultenuosly)

3. I have a workaround where I enabled the on board intel hd audio, and used the line in from that card which for some reason shows up as stereo input in the connections.

4. My guess is the Turtle beach TBS-3300 card driver may be an issue.

Although I have managed to solve my immediate issue of getting a line-in stereo connection using a second sound card, I could not find a sound card specific solution.

---

### Post by pramodbutte on 2010-10-01
Thanks for your input. This is what I have found so far,

1. In Maverick, pulse is not killed when jack server is started.

2. In the jack preferences, you have to specifically choose the input from line-in (Jack connections is not showing line-in and mic-in simultaneously)

3. I have a workaround where I enabled the on board intel hd audio, and used the line in from that card which for some reason shows up as stereo input in the connections.

4. My guess is the Turtle beach TBS-3300 card driver may be an issue.

Although I have managed to solve my immediate issue of getting a line-in stereo connection using a second sound card, I could not find a sound card specific solution.

---

