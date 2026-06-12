---
title: "aMSN, Mercury Video conferencing, and VLC via FTP advice needed..."
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by muso on 2007-04-25
I currently use aMSN for video, and have been using Skype for audio.  However, I've recently seen indications that aMSN may have full videoconferencing capabilities that have been disabled due to lack of support:

1. Is there a way of adding it back into aMSN, in Feisty?
2. Does anyone know when Farsight might be incorporated into aMSN?

Or, alternatively, has anyone got any experience of [Mercury]("http://www.mercury.to/")?  Does this handly video-conferencing any better?


n00b alert!  Potentially really stupidly easy question:
Also, as a slight aside, I have a NAS hard-drive.  It works with SMB and FTP protocols, but in SMB it's far too slow to stream video.  What's the easiest way of connecting to, for example, an AVI file via FTP? (I think VLC can support that, but when I click on an FTP file, it says it can't access it)

---

### Post by muso on 2007-05-01
Okay... I found this:
[AMSN and audio/voice chat capability?]("http://amsn-project.net/forums/viewtopic.php?p=11441&highlight=&sid=b506d363344337f2f42a49f8ba5d61c8")

"2 - the codec needed for encoding and decoding the voice is proprietary to microsoft and is not known by anyone (apart from me.. see below) and we can't implement it until someone reverse engineers the codec which is a lengthy process that noone wants to do... "

And this was in Jan 2007:

"SVN version 7848 now has full support of voice clips (sending and receiving), and I got news about the voice conversation feature, it might be doable and easier than we thought, I'll keep you posted."

---

### Post by muso on 2007-05-01
Another reply from the Site Admin there 26 Apr 2007:
[http://amsn-project.net/forums/viewtopic.php?t=3187](http://amsn-project.net/forums/viewtopic.php?t=3187)
"voice clip support is available in the svn version, otherwise for full duplex, real time voice, no, nothing is done and stop asking."

So I guess that this means that I'll have to look elsewhere than aMSN for a full video conferencing solution...

SightSpeed was another option I looked at, but contrary to their FAQ it looks like they have abandoned the idea of releasing a Linux version - probably to do with their reliance on proprietry IE technology for programming they have done on it.

Does anyone have any other suggestions - other than Ekiga and Net Meeting (or the currently unstable test version of Ekiga for Windows)?

I've looked more at Mercury, and it doesn't look like what I need.

Plus I still have the problem (less crucial) of streaming video files from an FTP server (unless I can get SMB to run as fast as it should be capable of...)

Thanks in advance...

---

### Post by loell on 2007-05-03
actually you can do voice to msn users using gtalk2voip service
with any sip base softphones availabe for linux

(gizmo , ekiga, linphone, wengophone , twinkle)

---

### Post by muso on 2007-05-03
> **loell said:**
> actually you can do voice to msn users using gtalk2voip service
with any sip base softphones availabe for linux

(gizmo , ekiga, linphone, wengophone , twinkle)

Thanks, that certainly looks like an alternative viable option, although... :) 

The person I'm video conferencing (who's using XP) has a problem with Skype because it ends up using 100% of the CPU, and even for sound only, it can cause problems.  The video we get in aMSN / MSN stutters a little more, but it works a lot better for most of the time.  She doesn't like NetMeeting at all, so the Ekiga/Netmeeting option is out.

So, I can only use aMSN for video, and I can't use the same (MSN) account twice: myself and my partner on the other end of the call both need to use one application and account for audio conversation, and another for the webcam.

But it looks like I can use GoogleTalk or Yahoo! with your suggestion, so I'll check that out tonight.

---

### Post by loell on 2007-05-03
:guitar:  its likes this, at you're end, you'll likely to use amsn for video and ekiga for voice (in this example, since ekiga is installed by default),  then configure a sip account, ekiga account or any sip provider will do.

advise her to accept a buddy invitation from gtalk2voip , you can invite her through [http://www.gtalk2voip.com/index.shtml]("http://www.gtalk2voip.com/index.shtml") , just type in her address ie(account_name@msn.com) and select MSN/live messenger in the combobox then Invite. now she'll have gtalk2voip as one of her buddy.

in order to call her, in ekiga, type in with this convention ( sip:user_at_domain.com@msn.gtalk2voip.com) where domain.com is replace most probably with "msn.com".

the call will then be directed through her msn/lve messenger :)  , so, she will only be using msn/lve messenger on her end, while you'll be using amsn for video and ekiga for voice at your end.

---

### Post by muso on 2007-05-03
Cool!  You're a true star, loell!  I'll check it out later, and let you know how I get on...

One step closer to ridding myself of XP... that makes me so happy! :biggrin:

---

### Post by muso on 2007-05-04
Hmm... no joy so far.  All I get is "Abnormal call termination" in Ekiga.  I'll check this weekend, but I'm sure that I have the router configured for SIP, and I don't see that anything else would cause a problem (I have used Ekiga with NetMeeting with the same setup, after all).

---

### Post by loell on 2007-05-04
try calling sip:500@ekiga.net its the echo test number, see if you can call through ekiga. 

there is also another route, you can also install gizmo since its also sip base.

---

