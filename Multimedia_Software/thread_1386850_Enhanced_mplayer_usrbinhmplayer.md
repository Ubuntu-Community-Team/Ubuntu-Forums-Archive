---
title: "Enhanced mplayer: /usr/bin/hmplayer"
date: 2010-01-21
forum: Multimedia Software
---

### Post by frenchn00b on 2010-01-21
Hello,

Many website have rather difficult streams, to be handled. 

I am pleased to provide your /usr/bin/hmplayer.

Best regards

---

### Post by mc4man on 2010-01-21
A few things
First your attacment is not a .gz, just a .tar

Second being just a script you may have wanted to also post it so people could see.

Actually did try as just a script (in ~/bin) and does work. - not inclined to run the installer, no need here and just in general

script

```
#!/bin/sh
# /usr/bin/hmplayer
# (h)mplayer, as enHanced mplayer
  


##tested with mplayer -playlist "http://www.bbc.co.uk/worldservice/meta/tx/nb/live_ennws_au_nb.asx"  && status="failed"
mplayer -playlist "$1" && status="failed"

if [  "$status" = "failed"  ]  ; then
   echo "Starting the url link fetcher ..."          
   mkdir "/tmp/hmplayer-$(whoami)"
   wget -k "$1"  -O "/tmp/hmplayer-$(whoami)/hmplayer.0"
   cat "/tmp/hmplayer-$(whoami)/hmplayer.0"  | grep -o 'http:[^"]*'   >     "/tmp/hmplayer-$(whoami)/hmplayer.1" 
   echo "Found the URL : " `cat /tmp/hmplayer-$(whoami)/hmplayer.1`
   mplayer -playlist `cat /tmp/hmplayer-$(whoami)/hmplayer.1`
   
fi

```

---

### Post by frenchn00b on 2010-01-21
Cool... I am really happy that there is some feedback and I appreciate a lot your comments. Thanks I am glad to learn. 

tar cvf I used to make the tar.gz format. I always thought that it was the best way... ok, i'll check out how to make better
tar xvfpz I use to unpack usually.

So, concerning the hmplayer: 
dont you think that it is strange that mplayer (not hmplayer) cannot simply seek deeper into the stream url? 

I think that this hmplayer has lot lot of benefits: hmplayer permits to play any kind of stream.

To come to this question: 
since mplayer is the rolls-royce of the multimedia video/music player: 
why they havent code mplayer yet to be capable of seeking the website better?  I mean the stream was there, not too complex to find. 

I am sure if this hmplayer would be known, it would be interesting for a mass amount of users, because believe me, lot of linux users do mplayer streaming... 

Well, ... bit surprised that mplayer cannot.

Thank you for your positive comments, they are super.

---

