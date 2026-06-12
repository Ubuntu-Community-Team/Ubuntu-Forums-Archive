---
title: "300 Channel DVR - A Project / Discussion"
date: 2014-06-26
forum: Mythbuntu
---

### Post by senator32 on 2014-06-26
Hello Mythbuntu forums! I seek the wisdom of you wise sages. 

I have been tasked to build a system for a research project where a massive number of TV channels from around the world are recorded 24/7, 365. The subsequent recordings are analyzed and stored for up to one year (a massive amount of storage...I know - even after transcoding with Mythbrake!). 

I have set about building Mythbuntu DVR systems with 12-24 tuners per box (three to six dual tuners + multiplexing twice per tuner), but I was wondering how you all would tackle this using Mythbuntu. This is my first time working with MythTV on this scale and I have plenty to learn about the platform.

Questions that come to mind are: 
[LIST]
[*]What is the best schema to array so many DVRs? As separate front-end + back-end systems or with one front-end and several connected back-ends? Currently, I am building independent systems that have both a primary front and back end.  
[*]I am having to transcode all of these channels in faster than real-time after the recording finishes in order to keep up with the rate of recording. Any suggestions on fast transcoding methods? I am using Mythbrake and going to H264 mp4 using the default settings. 
[*]As hinted above, space is a primary issue. Any suggestions on MythTV settings that can help with this? Other than the previously mentioned transcoding. 
[*]In order to save time, instead of having each machine scan for channels on each tuner, can I set all of the channels via mysql or setting? In this setup the channel lineup to each box is the same and never changes. 
[*]Any general suggestions?
[/LIST]

Current DVR test setup: 

Processor: 3.4Ghz i7
Ram: 32GB DDR3
Tuners: Hauppauge 2250 (x3)
OS: Mythbuntu 12.04 (I can post more specifics if needed)

I appreciate any discussion or suggestions on this topic. Thanks!

---

### Post by tgm4883 on 2014-06-27
I'm double posting my response since I seem to have broken out of the reply in the previous one and I don't want to mess with that one since I reported it as a bug.

Answers in-line

> **senator32 said:**
> 
Questions that come to mind are: 
What is the best schema to array so many DVRs? As separate front-end + back-end systems or with one front-end and several connected back-ends? Currently, I am building independent systems that have both a primary front and back end.  


You'll need multiple backends to handle that many channels. I don't see why you would need to have the backends as independent systems, just ensure that your mysql DB is tuned and on fast storage.

> **senator32 said:**
> 
I am having to transcode all of these channels in faster than real-time after the recording finishes in order to keep up with the rate of recording. Any suggestions on fast transcoding methods? I am using Mythbrake and going to H264 mp4 using the default settings. 


Why are you transcoding at all? I find this silly for two reasons.

1) This is obviously a big archiving project that will cost some money. Why are you skimping out on storage? Seems like you are setting yourself up for failure.
2) Why are you not using tuners that give you an h.264 stream to begin with. Why transcode it when you can get the stream the way you want from the tuner.

> **senator32 said:**
> 
As hinted above, space is a primary issue. Any suggestions on MythTV settings that can help with this? Other than the previously mentioned transcoding. 


See above answer.

> **senator32 said:**
> 
In order to save time, instead of having each machine scan for channels on each tuner, can I set all of the channels via mysql or setting? In this setup the channel lineup to each box is the same and never changes. 


If they are all connected, then you only need to setup/scan the channel lineup once and just add it in each backend.

> **senator32 said:**
> 
Any general suggestions?


> **senator32 said:**
> 

Current DVR test setup: 

Processor: 3.4Ghz i7
Ram: 32GB DDR3
Tuners: Hauppauge 2250 (x3)
OS: Mythbuntu 12.04 (I can post more specifics if needed)

I appreciate any discussion or suggestions on this topic. Thanks!

There is quite a bit missing from your post which makes me think that A) You've not done enough research into this, and B) You don't know enough about how MythTV works. I would recommend researching what others that have used MythTV for a similar (although IIRC a smaller scale) project have come up with.

Questions I have (off the top of my head)
1) If you are transcoding, you'll need more processor. A lot more processor (again, why transcode if you don't have to). I hope you have servers dedicated to just transcoding it. Once you transcode it, are you keeping it in MythTV? Will MythTV be your frontend for viewing?
2) How do you plan on recording "a massive number of TV channels from around the world are recorded 24/7, 365" when you've listed a tuner that uses a standard primarily in the US?
3) What type of storage are you going to use for this, and have you verified it can write fast enough for the number of streams you want to record?
4) Why so much RAM?

---

### Post by senator32 on 2014-06-28
Thanks for your quick reply! I would have been quicker to write back but have been AFK all day. 

> You'll need multiple backends to handle that many channels. I don't see why you would need to have the backends as independent systems, just ensure that your mysql DB is tuned and on fast storage.


This is what I was thinking. The only reason why the current systems are independent was for hardware testing and for me to get generally familiar with the MythTV system at this scale. I will take your suggestion in the next test setup. 

> Why are you transcoding at all? I find this silly for two reasons.

1) This is obviously a big archiving project that will cost some money. Why are you skimping out on storage? Seems like you are setting yourself up for failure.
2) Why are you not using tuners that give you an h.264 stream to begin with. Why transcode it when you can get the stream the way you want from the tuner.

1 - Not sure how I am skimping on storage, as I am looking at about $100,000+ SAN storage solutions :) but I love your general point. Why record in the massive MPEG TS if I don't need to. 
2 - This is an eye-opening response for me. I would LOVE to record directly to smaller H264 Mp4 from the tuners without the need to transcode, but I was under the impression (and every tuner I have had for the last 10 years has been this way) that TV tuners recorded the MPEG Transport stream, and the only way to get it to a usable program stream like mp4 (and to save space) was to transcode it. 

[B]What tuners do you suggest that would record native in MP4? (I am doing some Googleing on that myself now). This would solve almost all my problems if true. 
[/B]
> Questions I have (off the top of my head)
1) If you are transcoding, you'll need more processor. A lot more processor (again, why transcode if you don't have to). I hope you have servers dedicated to just transcoding it. Once you transcode it, are you keeping it in MythTV? Will MythTV be your frontend for viewing?
2) How do you plan on recording "a massive number of TV channels from around the world are recorded 24/7, 365" when you've listed a tuner that uses a standard primarily in the US?
3) What type of storage are you going to use for this, and have you verified it can write fast enough for the number of streams you want to record?
4) Why so much RAM?

As for "a bit missing from your post", I am willing to post any information you think is relevant, I just wanted to get the conversation started. While I feel like I have a pretty firm grasp on the setup and general day-to-day of MythTV, this project is has a very large scope and scale and I can use all the input I can get from more experiences users, such as yourself. 

1 - In the currently setup I would have massive servers dedicated to transcoding. I am hoping, based on your previous response, that I may be able to find a tuner that records TV directly in smaller mp4, then this transcoding will not be as necessary. 
2 - The institution I am working on this project with has satellite feeds from DishTV from around the world. They provide the channel lineup and access to content. In the immediate future, I will be focusing on US content. 
3 - The type and speed of storage was a concern early on, but what I have found is that even a machine recording with 12 tuners at once only uses between 7 - 50 MBps which is very manageable with RAIDs and traditional HDDs. Long term storage will be large rack systems of SANs or similar. 
4 - This i a good point. I doubt the amount of ram that is in the test setup is required. In the most recent DVR I made this week, I only used 8GB of RAM and things worked out ok. 

I appreciate the response, and look forward to more dialog.

---

### Post by senator32 on 2014-06-28
Also, forgot to respond to: > Once you transcode it, are you keeping it in MythTV? Will MythTV be your frontend for viewing?

No, once MythTV records the program, I have scripts that move the files to the network storage. We are not interested in using the Myth Front-end to view and manage all the recordings. Really just using the MythTV services for the backend DVR.

---

### Post by senator32 on 2014-07-01
Does anyone know of a tuner that would record directly from Coax QAM to MP4 H264? I have done some research and despite the claim above, I am not sure it exists. I have found products like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116086](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116086) , however, they require an HDMI input and do not have a TV tuner. Even so, I might be willing to make sure gear work, but from what I can see that product does not support Linux. 

Any suggestions Mythbuntu forums? 

Thanks again!

---

