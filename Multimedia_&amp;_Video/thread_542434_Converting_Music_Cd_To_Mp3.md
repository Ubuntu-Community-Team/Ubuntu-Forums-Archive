---
title: "Converting Music Cd To Mp3"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by hatewindows on 2007-09-03
Hello all-I was wondering if there was a simple program that will convert cd music to mp3 format in Ubuntu?  Thanks for any help!  Have a great night!! MARK

---

### Post by wolfen69 on 2007-09-03
applications>sound & video>sound juicer cd extractor

---

### Post by hatewindows on 2007-09-03
I dont see an MP3 option in sound Juicer?  I must be missing something...

---

### Post by wolfen69 on 2007-09-03
after you open it, go to edit>preferences>pull down menu at the bottom.

---

### Post by aysiu on 2007-09-04
You have to install *gstreamer0.10-plugins-ugly-multiverse* first, I think, before MP3 will appear as an option in the pull-down menu.

More details here on installing software:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by rhodry on 2007-09-04
> **wolfen69 said:**
> applications>sound & video>sound juicer cd extractor

I find abcde from a cli (Terminal) gives the best results. Here is a link to a great little 'howto':

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

Cheers,
Rhodry.

---

### Post by rsambuca on 2007-09-05
> **rhodry said:**
> I find abcde from a cli (Terminal) gives the best results. Here is a link to a great little 'howto':

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

Cheers,
Rhodry.

Why would that give "the best results"?  It uses the lame mp3 encoder just as Sound Juicer does.

---

### Post by rhodry on 2007-09-05
> **rsambuca said:**
> Why would that give "the best results"?  It uses the lame mp3 encoder just as Sound Juicer does.

I did say "I find". Would you prefer "In my opinion" or "For me" or "In my experience"?

I was expressing a personal opinion that might help the OP look at some alternatives, is all.

I am well aware of what codecs Sound Juicer uses and it's a perfectly acceptable alternative. I happen to prefer the flexibility of setting the command line options (to try different quality options) as I write the command on the cli, rather than having to open Sound Juicer, Edit Preferences, Edit Profiles, highlight the codec option line, then type options.  Also, I have more than one cd drive to rip from and I find a simple change of one letter in a command easier.

If you read my post as some advocacy for the underlying codec, then you have misinterpreted my intention. I will try to be more specific for you in future.

Rhodry.

---

### Post by rsambuca on 2007-09-05
> **rhodry said:**
> I did say "I find". Would you prefer "In my opinion" or "For me" or "In my experience"?

I was expressing a personal opinion that might help the OP look at some alternatives, is all.

I am well aware of what codecs Sound Juicer uses and it's a perfectly acceptable alternative. I happen to prefer the flexibility of setting the command line options (to try different quality options) as I write the command on the cli, rather than having to open Sound Juicer, Edit Preferences, Edit Profiles, highlight the codec option line, then type options.  Also, I have more than one cd drive to rip from and I find a simple change of one letter in a command easier.

If you read my post as some advocacy for the underlying codec, then you have misinterpreted my intention. I will try to be more specific for you in future.

Rhodry.

Sorry if I offended you.  I (obviously in error) thought your phrase "gives the best results" to refer to the quality of the resulting mp3.  I didn't see any statement referring to the configurability, set-up, etc.

---

### Post by andrew.46 on 2007-09-11
Hi,

 Saw a discussion about my walkthrough:

> **rsambuca said:**
> Why would that give "the best results"?  It uses the lame mp3 encoder just as Sound Juicer does.

 True, the encoder is the same. The best bit with the abcde script is the power it hands you to change many, many settings by a simple file: ~/.abcde.conf; or if you have the skills to change the script itself.

 Another difference you will notice is the relative speed of both programs, but I will leave you to judge this yourself :-)

 Simple changes that can be made to the lame settings within abcde can be a choice of the following 3 quality settings:

```
LAMEOPTS='--preset standard'
LAMEOPTS='--preset extreme'
LAMEOPTS='--preset insane'
```

 Can I suggest you try the program and have a twiddle with the settings? Try ogg encoding / flac encoding, explore the myriad of options with encoding / commenting / tagging / altering sound levels etc etc.  If you are not happy with it your money will be refunded :-)

             Andrew
             [http://people.aapt.net.au/~adjlstrong/ubuntu.html](http://people.aapt.net.au/~adjlstrong/ubuntu.html)

---

### Post by rsambuca on 2007-09-11
Hey, I don't doubt that abcde is a highly configurable and powerful program, but I just thought rhodry's use of the words "best results" were misleading.  By definition, the word 'results' refers to the final product, and has nothing to do with speed, configurability, etc.  His next post (post #8) explained it perfectly.

---

