---
title: "How do I record every instance of a show?"
date: 2011-11-22
forum: Mythbuntu
---

### Post by bpmod on 2011-11-22
Hello

I have been very happy with Mythbuntu and MythTV since installing it a week or two ago. I initially installed only one tuner because I needed to get it up and running quickly.

However, I now have three tuners connected, and am experiencing issues.

My tuners are:
HDHomeRun Dual (2 tuners)
Hauppauge WinTV-Hvr_1250 (single tuner)

I would like to record every airing of a particular show (usually twice daily, same episode). Today was the first time that I had the HDHomeRun installed when the show aired. I have now checked my Recorded Shows, and find that the two recordings of my show are shown as recorded, but one shows a size of B and I cannot find the corresponding recording. It does not exist in the Recordings directory.

After looking through all of the documentation I can find, I have come to the conclusion that MythTV is written to prevent me from recording the same episode of the same show more than once. How do I override this and tell it to record EVERY time that show airs?

Thanks

Brian

---

### Post by nickrout on 2011-11-23
Firstly, if you can tell us why precisely you would like to record the same episode twice, we could perhaps look at workarounds fronm the usual and sensible behaviour of avoiding repetitions.

Secondly recordings with B length have tried to record, but failed, usually due to a hardware or driver or tuning (as in inability to tune) issue. Look at your backend log and it may tell you why the B recording failed.

Third, try setting Duplicate Detection Method in the recording rule, it should achieve what you want :)

---

### Post by bpmod on 2011-11-23
> **nickrout said:**
> Firstly, if you can tell us why precisely you would like to record the same episode twice, we could perhaps look at workarounds fronm the usual and sensible behaviour of avoiding repetitions.
*Ours is not to wonder why...* I cannot possibly be the only person to have missed an episode of his favourite show because of limitations of recording hardware and/or software. How many times have I set my VCR, DVR, etc. to record, only to come home and discover that the President (of a foreign country) had something important to say, or that the show was pre-empted for infomercials, or the weather prevented my antenna from picking up *that station* at *that time*? So, the answer of course is duplicity and redundancy. Even now, during 6 years of recording my favourite show twice per day, I have missed episodes (which will never again be broadcast anywhere).
> Secondly recordings with B length have tried to record, but failed, usually due to a hardware or driver or tuning (as in inability to tune) issue. Look at your backend log and it may tell you why the B recording failed.OK. This, I suppose, answers part of the question. It seems that I had unwittingly set (one tuner of) the HDHomeRun as a priority on another machine on the network, shown by this:
```
2011-11-22 19:29:02.455 HDHRSH(10314DDB-0) Error: DeviceSet(channel 8vsb:617000000): ERROR: resource locked by 192.168.0.151
```and then this:
```
2011-11-22 19:29:02.473 HDHRSH(10314DDB-0) Error: DeviceSet(channel auto:617000000): ERROR: resource locked by 192.168.0.151
```Of course, the part it didn't answer was, why, when it couldn't get HDHRSH(10314DDB-0), it didn't try HDHRSH(10314DDB-1) or the Hauppauge tuner (whichever one was not then currently in use)? But that was immediately followed by:
```
2011-11-22 19:29:02.479 Started recording: TVShow!: channel 1071 on cardid 3, sourceid 1
2011-11-22 19:29:02.500 SignalMonitor: channel change failed
2011-11-22 19:29:02.564 SignalMonitor: channel change failed
2011-11-22 19:29:02.621 SignalMonitor: channel change failed
2011-11-22 19:29:02.679 SignalMonitor: channel change failed
2011-11-22 19:29:02.738 SignalMonitor: channel change failed
2011-11-22 19:29:02.794 SignalMonitor: channel change failed
2011-11-22 19:29:02.852 SignalMonitor: channel change failed
2011-11-22 19:29:02.909 SignalMonitor: channel change failed
2011-11-22 19:29:02.968 SignalMonitor: channel change failed
2011-11-22 19:29:03.038 SignalMonitor: channel change failed
2011-11-22 19:29:03.095 SignalMonitor: channel change failed
2011-11-22 19:29:03.152 SignalMonitor: channel change failed
2011-11-22 19:29:03.214 SignalMonitor: channel change failed
2011-11-22 19:29:03.893 Updating status for TVShow! on cardid 3 (Tuning => Recorder Failed)

```And why, further, does the recording show in my recordings list with no errors or any somesuch?
> Third, try setting Duplicate Detection Method in the recording rule, it should achieve what you wantMy setting for Duplicate Detection Method is 'none'. Is that supposed to record all eps, regardless of anything else?

Thanks

Brian

---

### Post by nickrout on 2011-11-23
Well there's your error, you can't use the HDHR from another machine, myth needs sole access to the HDHR. You will have to live with that, don't let other machines use it.

---

### Post by bpmod on 2011-11-23
> **nickrout said:**
> Well there's your error, you can't use the HDHR from another machine, myth needs sole access to the HDHR. You will have to live with that, don't let other machines use it.
OK, fixed.

But that totally defeats the purpose of the HDHomeRun (as opposed to an internal tuner).

I will install another two tuners (already purchased) into my Myth backend, so it doesn't happen again.

Thanks

Brian

---

### Post by nickrout on 2011-11-24
> **bpmod said:**
> OK, fixed.

But that totally defeats the purpose of the HDHomeRun (as opposed to an internal tuner).That depends on what you think it's purpose is. The fact that[LIST=1]
[*]it is reliable and isn't subject to the vagaries of kernel updates; and
[*]means that you can locate the tuner at a separate location to the backend ; and
[*]does not take up a pci slot in the backend
[/LIST]are all legitimate reasons to use an HDHR> 

I will install another two tuners (already purchased) into my Myth backend, so it doesn't happen again.

Thanks

Brian

Certainly if you want to use your HDHR's on computers elsewhere on your network, that is a better option for you.

Of course you could also consider installing mythfrontend on those other computers, and accessing everything through mythtv.

---

### Post by bpmod on 2011-11-28
> **nickrout said:**
> That depends on what you think it's purpose is. The fact that
[LIST=1]
[*]it is reliable and isn't subject to the vagaries of kernel updates; and
[*]means that you can locate the tuner at a separate location to the backend ; and
[*]does not take up a pci slot in the backend
[/LIST]
are all legitimate reasons to use an HDHR

Certainly if you want to use your HDHR's on computers elsewhere on your network, that is a better option for you.

Of course you could also consider installing mythfrontend on those other computers, and accessing everything through mythtv.
1. To say that the HDHR is more reliable than any other given piece of hardware is stretching it at best.
2. The **only** reason to locate it away from the computer is for the purpose of using it on more than one computer. **(That's what I thought the purpose of it was.)**
3. When you've got 4 PCI slots not in use, this becomes moot.

It turns out that it wasn't enough to not use (or allow the other computers to use) the HDHR at the time I wanted to record. I had to take the HDHR software off of every other computer on the network before MythTV would use it.

But now, I have three tuners in addition to the HDHR, and it **still** won't record off of it. I guess I have to tell it explicitly.

My earlier question was not answered though: Why, when there has been nothing recorded, does the results (recorded TV shows list) show that the program was recorded with no error (other than the B, which, if you don't know what it means, doesn't tell you anything)?

And, now I guess I have another question (which was asked before, but now the situation has changed): Why does MythTV continue to "record" after it encounters an error (such as not being able to tune a station). Or, why does it not try a different tuner?

Even now that I have missed several programs, it is telling me that it is recording a show and has another two shows after that one (on the same station) to be recorded on the same encoder, while that encoder can not lock in that station.

It is really frustrating to have 10 encoders installed and not be able to record a single thing.

And, I have now tried to make it use a different encoder, but it won't budge. Is there something I can do to make that happen? I have selected the HDHR instead of 'any' in the preferred input list, but that doesn't do it.

Oh, and I am limited to the hardware at hand. I do not have another computer that I can install mythfrontend on. Maybe you have enough money to go out and buy another computer to use as a frontend at the drop of a hat, but I don't have that luxury.

I really really think that MythTV would be a good solution if it would just do what (I think) it's supposed to.

I almost took my Windows computer offline on the weekend, because I thought I had found a permanent solution, but I guess it's going to stay. And, no, MythTV is not an option on that one, even if MythTV would work, as the hardware is not compatible with Linux.

Thanks

Brian

---

### Post by nickrout on 2011-11-29
> **bpmod said:**
> 1. To say that the HDHR is more reliable than any other given piece of hardware is stretching it at best.Certainly not a common view, most people find them very reliable> 
2. The **only** reason to locate it away from the computer is for the purpose of using it on more than one computer. **(That's what I thought the purpose of it was.)** you are illogical captain. Consider a scenario (common) of the only antenna connection is in the lounge, but you want the noisy hot backend in the basement. Put the HDHR in the loungge and network it to the basement> 
3. When you've got 4 PCI slots not in use, this becomes moot.for you maybe :)> 

It turns out that it wasn't enough to not use (or allow the other computers to use) the HDHR at the time I wanted to record. I had to take the HDHR software off of every other computer on the network before MythTV would use it. as previously advised mythbackend requires exclusive use of each tuner in the system, including HDHRs> 

But now, I have three tuners in addition to the HDHR, and it **still** won't record off of it. I guess I have to tell it explicitly.

My earlier question was not answered though: Why, when there has been nothing recorded, does the results (recorded TV shows list) show that the program was recorded with no error (other than the B, which, if you don't know what it means, doesn't tell you anything)?I do not know, ask a developer on the mailing list> 

And, now I guess I have another question (which was asked before, but now the situation has changed): Why does MythTV continue to "record" after it encounters an error (such as not being able to tune a station). Or, why does it not try a different tuner?

Even now that I have missed several programs, it is telling me that it is recording a show and has another two shows after that one (on the same station) to be recorded on the same encoder, while that encoder can not lock in that station.

It is really frustrating to have 10 encoders installed and not be able to record a single thing.then you are doing something wrong.

Go back to basics, obviously you need to remove the HDHR from the myth setup, as you don't want to give myth exclusive use of them.

Then record something on your other tuner, and if it fails show us your backend log around the failure.> 

And, I have now tried to make it use a different encoder, but it won't budge. Is there something I can do to make that happen? I have selected the HDHR instead of 'any' in the preferred input list, but that doesn't do it.

Oh, and I am limited to the hardware at hand. I do not have another computer that I can install mythfrontend on. Maybe you have enough money to go out and buy another computer to use as a frontend at the drop of a hat, but I don't have that luxury.

I really really think that MythTV would be a good solution if it would just do what (I think) it's supposed to. it does what it is designed to do, but if your internal tuners are not working, we need to see a backend log.> 

I almost took my Windows computer offline on the weekend, because I thought I had found a permanent solution, but I guess it's going to stay. And, no, MythTV is not an option on that one, even if MythTV would work, as the hardware is not compatible with Linux.

Thanks

Brian

---

