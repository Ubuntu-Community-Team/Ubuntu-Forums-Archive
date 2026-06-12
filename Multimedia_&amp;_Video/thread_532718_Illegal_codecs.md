---
title: "Illegal codecs???"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by gimpguy2000 on 2007-08-23
I was wondering...as I don't know which codecs specifically cannot be installed in Ubuntu, is there a list where i could remove if need be? I am not even sure which codecs I have installed, being a newbie, I would simply like to know which exact libs and such are not allowed. Anyone have a list?

TX

---

### Post by aquavitae on 2007-08-23
Are you asking which codecs are available in ubuntu, or which are legal in ubuntu?  

What's legal depends on what country you are in, and to be quite honest, most linux users don't seem to worry too much about that!   If you're using gstreamer as your media player (frontends include totem) which you probably are if you're on ubuntu (instead of kubuntu), then its separated into 3 packages - good, bad and ugly.  You can look for them in synaptic to see the exact differences, but as far as I know, the legality of those included in bad and ugly is questionable.  I could be quite wrong about this so hopefully someone will correct me.

If you want to know what codecs are available in ubuntu - practically all of them.  I haven't yet seen any media format which cannot be played.  Some of the more obscure one may be a bit more difficult to get, but all the ones you are likely to need are included in the good, bad, ugly gstreamer packages.

I hope this answers your question.

---

### Post by gimpguy2000 on 2007-08-23
> **aquavitae said:**
> Are you asking which codecs are available in ubuntu, or which are legal in ubuntu?  

What's legal depends on what country you are in, and to be quite honest, most linux users don't seem to worry too much about that!   If you're using gstreamer as your media player (frontends include totem) which you probably are if you're on ubuntu (instead of kubuntu), then its separated into 3 packages - good, bad and ugly.  You can look for them in synaptic to see the exact differences, but as far as I know, the legality of those included in bad and ugly is questionable.  I could be quite wrong about this so hopefully someone will correct me.

If you want to know what codecs are available in ubuntu - practically all of them.  I haven't yet seen any media format which cannot be played.  Some of the more obscure one may be a bit more difficult to get, but all the ones you are likely to need are included in the good, bad, ugly gstreamer packages.

I hope this answers your question.

Hi, thanks for the info but i'm still stuck. I want to uninstall some as some of them say, if illegal in your country but doesn't say which country they are illegal in?? LOL. That really helps. 
  
So basically I wanted to know if there is a list of illegal plugins for the US so if I have any, they can immediately be uninstalled. Also, I read through the forums and such and have been warned by others in other forums to watch for these. 

 Simply I want to get rid of them and if need be, Ubuntu as well. I had no idea there was no DVD codec support in Linux distros.  Well, just when I was happy with Ubuntu, I hear this. See, when I saw the warnings, I automatically assumed it was illegal in other countries, I mean, there are codecs all over the place but seems restricted to Windows OS and programs associated with.  My shock was when I found they were illegal in mainly the US. :(  For pete sakes, even these are illegal....Well if I can't use dvd stuff on a Linux distro, not much point in using it at all. 

BTW: I blame no one but myself for my misunderstanding, just bites though.

---

### Post by aquavitae on 2007-08-23
Hmm, that's going onto shaky ground.  If you look on google you'll find quite a lot about the relative legallity of linux in general.  The linux kernel iteslf technically breaks some microsoft patents, but but on the other hand microsoft have patented stuff which wasn't their's in the first place.  My personal view is I'd rather break a law (one that I don't think should be there anyway) than support a corrupt, meglomaniacal corporation.  I.e. its a matter of personal ethics.  If you decide to follow the letter of the law regardless of whether its right or wrong, thats up to you.

I don't know which codecs (or even which software) is illegal (in US) in linux, but I think they are all in ther restricted repository.  You can disable it in synaptic, and remove any thing that's already installed from it.

EDIT: Legal media formats do exist in linux, e.g. the ogg music format.  If you stick to those then you'll be fine.  For a discussion on legal/illegal codecs look here: [http://ubuntuforums.org/showthread.php?t=43877]("http://ubuntuforums.org/showthread.php?t=43877")

---

### Post by gimpguy2000 on 2007-08-23
Thanks for the info. 

After reading just about every type of forum issue on codecs...I have come to this conclusion..

The way codecs and such are patented, is simply cornering the market and stifling progress. The "supposed" legal aspect becomes illegal in many ways. I don't feel many should be illegal. Truly, you buy a DVD and it's actually illegal to play in some aspects?? I think our laws need tearing down and rebuilding. I was just on a conversation a while back and it was all about how large corporations abuse patent laws, this seems no different. 

 While I don't know if I have any of these codecs installed, too bad. That is definitely screwed up. So even if open source codecs were developed, they would still be illegal really as it seems the patent is on the codec source so no matter what, it limits use and rights. Think that wasn't set up that way? Hmmmmm. Yeah, it was definitely drawn out in such a way. 

With any luck, they will simply do away with these patents, or , at least, they SHOULD.  


TX again,

---

### Post by aquavitae on 2007-08-24
My view exactly!
> With any luck, they will simply do away with these patents, or , at least, they SHOULD. 
I agree, but I dounbt they will unfortunately.  Too much money behind them... :(

---

### Post by fredj on 2007-08-24
The problem in the U.S. is nothing to do with patents. It is simply this. The DVD industry i.e. the 
major movie studios have always refused to allow DVD codecs for Linux. So Linux users had to
make their own DVD codecs by reverse engineering the windows ones. This may be illegal
in the U.S. under the terms of the DCMA laws since technically it could be construed as bypassing
a security system. No prosecutions have ever been taken against users playing DVDs legally
owned by them under Linux. 

The movie studios tried to sue the people who made the original decoders for commercial DVDs
under Linux in some European countries but they were unsuccessful.

---

