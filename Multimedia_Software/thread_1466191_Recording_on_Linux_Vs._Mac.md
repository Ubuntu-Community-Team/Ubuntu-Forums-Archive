---
title: "Recording on Linux Vs. Mac"
date: 2010-04-30
forum: Multimedia Software
---

### Post by Oasu4g on 2010-04-30
Hello,

I have a question about audio recording.

I've always wanted to set up a sort of personal studio. Not anything too professional, but I want to be able to make quality recordings without too many problems. All I'll probably end up using is a midi keyboard electric guitar and bass. But what I was wondering was, is it a better idea to get a Mac for something like that, or will Ubuntu support that just fine? I know there's great software available, and I've gotten used to using Jack. But I've read problems about real-time kernel support and xruns with Jack and Ardour, and I'm just wondering if that's something that will make using Ubuntu for this complicated.

Regards,

Tim

---

### Post by cchhrriiss121212 on 2010-04-30
I have a similar setup and ubuntu can handle everything I want very capably. The only complicated part about jackd is getting it setup correctly, and after that it is just a matter of learning how to get the most out of it.

> But I've read problems about real-time kernel support and xruns with Jack and Ardour...
I don't know what this might refer to, do you mean that lucid [will not have a realtime kernel]("http://ubuntuforums.org/showthread.php?t=1463455")?
Xruns occur when settings for jack are too much for jack to handle, or when something interferes with the audio chain. If you have the money to spend then a mac would be a no-brainer (as you could install jack on it as well), but I would try and see whether ubuntu works for you first as it won't cost you a penny.

If you want some good quality then you also should look at [supported soundcards]("http://ubuntuforums.org/showthread.php?t=1449800"), as they will really make a difference compared with onboard audio.

---

### Post by Oasu4g on 2010-05-08
Thanks cchhrriiss121212,

I don't know what specifically caused the xruns, but I was having trouble with them randomly, and I've read that they occur in linux frequently because the rt-kernel was not very compatible with Ubuntu. All of that is from memory, though. I can't give you specific links, and I'm probably confused about it anyhow. Thank you for clearing that up, though. I'll make sure to get a supported audio card for my next PC.

I appreciate your help,

Tim

---

