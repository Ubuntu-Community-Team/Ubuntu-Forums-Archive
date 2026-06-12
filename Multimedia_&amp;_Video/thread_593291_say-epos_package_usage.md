---
title: "say-epos package usage"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by stanigator on 2007-10-27
I saw the command **say "string"** somewhere on youtube on a mac os X machine and it pronounces the text. I installed say-epos on Ubuntu gutsy. However, I am having problems with it pronouncing the words (won't run properly) even though I installed it through Synaptic. Anyone have any ideas? Thanks.

---

### Post by hunt.topher on 2008-04-27
I have played with this command on Ubuntu too and I haven't had much luck either. :-( One thing I've found is that you have to start the epos daemon before it can say anything, with this command:
```
eposd & 
```
and then try:
```
say-epos "string"
```
as you did. This usually outputs out the string in the terminal with a bunch of #### marks. Under Gutsy I got it to make noises that were staticky but I could recognize the first syllable of my string, but under Hardy I haven't had any luck so far.

The Ubuntu repo site says that Say-Epos is an experimental project. Epos can't be *that* experimental because it works pretty well on macs! This feature is too fun to give up on... :-(

---

