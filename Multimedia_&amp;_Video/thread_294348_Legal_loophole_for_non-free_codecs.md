---
title: "Legal loophole for non-free codecs?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by mjukr on 2006-11-06
As I understand it, it is not legal for those who reside in the United States to install the w32codecs and other non-free codecs.

However, if I own a copy of say, Windows XP or Linspire or whatever other OS is purchased and contains those codecs, is it legal to then install those codecs on Ubuntu, assuming I don't have the other OS installed (just have the media)? Or are there other legal barriers to this?

Thanks for any pointers!

---

### Post by mazirian on 2006-11-06
This answer is off the top of my head, and as with any answer any member of these forums might give you, not intended to be legal advice. In other words, do not rely on this information for legal purposes. That said, I believe that all or most the codecs in the win32codecs package are subject to copyrights but are nonetheless freely available from their respective authors subject to a EULA.  The EULA prohibits redistribution of the codecs.  So it is illegal for ubuntu (or any other distro) to distribute those codecs to you, even though it is, I believe, legal for you to obtain them from their authors and use them regardless of whether you have a windows or any other license.  In other words, the legal worry is on the part of the person you get the codecs from and is not necessarily yours as an end user.

The same is not necessarily true for certain codecs, such as those that allow you to watch dvd movies.  There, you are dealing with a whole different creature of US law, the DMCA.

---

### Post by mjukr on 2006-11-06
Thanks for the quick reply! Makes sense. In the particular case of DVD playback, let's say I buy a commercial copy of PowerDVD or something similar that plays on Windows, yet don't use the license. Any idea if it would be considered legal to install libdvdcss with that in possession, or does installing it from a 3rd-party repository violate the DMCA restrictions outright? Thanks for any more advice!

---

### Post by mazirian on 2006-11-06
It is nonetheless illegal.  It is the dvd libraries themselves that are violative of the DMCA, unfortunately.

---

### Post by mjukr on 2006-11-07
Bummer... well, thanks for the great info!

---

### Post by mozetti on 2006-11-07
> **mazirian said:**
> It is nonetheless illegal.  It is the dvd libraries themselves that are violative of the DMCA, unfortunately.

That begs the questions, how does one legally obtain the files/libraries/et al needed to enable DVD playback on Ubuntu?

---

### Post by mazirian on 2006-11-07
Let's go back a step, because, as I understand it, there is still some uncertainty concerning the DMCA and what may constitue a violation of that law.  Distribution of the deCSS code that is in the libdvdcss package is illegal under the act, according to a series of federal appellate court decisions.  The RIAA and MPAA contend that playback of any encrypted dvd using that library is also a violation of the act as you are circumventing a copyright protection measure.  It's not clear that they are right.  I don't think there is a case that establishes such an interpretation of the DMCA yet. It may have even been foreclosed.  I haven't looked into this issue for a while.

In order to legally playback a dvd on ubuntu you would have to purchase a license to do so.  That's not going to happen easily.  I am confident, though I reiterate my disclaimers above, that whatever license is extended to the authors of PowerDVD or any similar dvd playback software for windows does not cover you for playback of a dvd on linux using decss.  Certain linux distrubutions, like Linspire, at some point purchased rights to distribute code for legal dvd playback (at least I vaguely recall them doing so), but no such license has ever been given to or purchased by ubuntu to my knowledge. In other words, the only option for now is to use the illegal code.

I urge anyone who has a concern for this issue to independantly read up on it.  I'm sure the EFF website would be a good place to start, but there is no substitute for reading the law at issue, which may be found [here]("http://www4.law.cornell.edu/uscode/html/uscode17/usc_sup_01_17_10_12.html")

---

### Post by mjukr on 2006-11-07
Which then begs the question... is there some way to get Linspire's DVD playback capability in Ubuntu? I mean, if I purchased Linspire, and there is just an RPM or other package for Linspire, wouldn't it be possible to then install it under Ubuntu? I suppose there might be some sort of license agreement catch, however.

Honestly, I'm surprised someone hasn't put together a "commercial" version of Ubuntu or at least an add-on pack for those looking for legal solutions to multimedia playback. I'd be first in line to snap it up!

---

### Post by handy on 2006-11-08
In my country it costs over $150,000, to cover the costs of a search warrant, you really do need to be worth it!

Some laws are really dumb & only protect corporate greed.

I would not go to too much trouble as a home user to protect myself from those dumb laws.

Those same dumb laws, in my country would cost you $65,000, every time you taped a show off the TV.

---

### Post by mjukr on 2006-11-08
For my personal use, I'm not so concerned. But when I try to explain it to other people who might want to use Ubuntu, I wish there was a Linspire-like version that had everything pre-packaged without needing to worry about grabbing "questionable" sources.

But I don't lose any sleep over it ;)

---

### Post by boban on 2006-11-08
I'm not a lawyer, and I'm not from US:), but I think if you have legally bought WinXp with those codecs, than you probably can use them in ubuntu... But you should check win EULA, to be sure...

---

### Post by mjukr on 2006-11-08
I'll need a pot of coffee to get through that Microsoft EULA without falling asleep! :p

---

### Post by mazirian on 2006-11-08
@boban: I'm not sure which codecs you're referring to, but with respect to the video codecs supplied in the win32codecs package, a license from Microsoft is irrelevant for the reasons stated above.  With respect to deCSS, a windows license is not going to make dvd playback any more legal than it is already (recall that the legality of playback using that code as opposed to its distribution is still an open question, although there are strong arguments that playback using the decss code should be perfectly legal, even if distributing it is not).

In my view, being required to pay for a license to view content you have already paid to view (either by purchasing or renting a dvd) is simply robbery, and we should be working to forestall any argument that US users are so prohibited under the DMCA rather than trying to find a way for linux users to pay for such a license.

---

### Post by boban on 2006-11-08
@mazirian: Thanks for clearing this out...

---

### Post by SnTholiday on 2006-11-08
> **mazirian said:**
> @boban: 
In my view, being required to pay for a license to view content you have already paid to view (either by purchasing or renting a dvd) is simply robbery, and we should be working to forestall any argument that US users are so prohibited under the DMCA rather than trying to find a way for linux users to pay for such a license.

I agree with this 100%! The only DVDs I would ever want to play on my Ubuntu system would be concerts/music I purchased, not illegally downloaded. In addition I have no intention of copying
them.

---

### Post by handy on 2006-11-09
@mazirian, I totally agree with you, the whole problem is corporate greed, as usual...

With only one small jump from the corporate we land at the shareholder!  So, really it just comes down to the consumer societies that we have been bought up in.  It is really hard to become objective about ***that one*** when you have known nothing else.

That is the problem facing our cultures today in the face of global climate change, individually we have to face the fact that there is a variety of toxic exhaustion as a result of our consumptions.

Strange as it may seem, there is very little that we do that is not connected to carbon being released into the atmosphere! (Just to pick on the primary toxic exhaustion problem)

As mazirian scratches his(?) head & says "how did **I** get connected with **that**?!"

---

### Post by mazirian on 2006-11-09
@Handy: I like how you draw that connection.  It's all about understanding the consequences of our consumption I suppose. Unfortunately for the planet, however, many people are more likely to care about the impairment of their media consumption, which is immediately inconveniencing, than their relationship to and effects on the planet.  The latter issue is easily dismissed by so many because it requires a meaure of scientific understanding or at least trust in the scientific method. On the other hand, explaining the value of free/open source and the effects of DRM isn't always that easy either.

---

### Post by handy on 2006-11-09
Too true...

---

### Post by Echo35 on 2006-11-09
> **mjukr said:**
> Which then begs the question... is there some way to get Linspire's DVD playback capability in Ubuntu? I mean, if I purchased Linspire, and there is just an RPM or other package for Linspire, wouldn't it be possible to then install it under Ubuntu? I suppose there might be some sort of license agreement catch, however.
 
Honestly, I'm surprised someone hasn't put together a "commercial" version of Ubuntu or at least an add-on pack for those looking for legal solutions to multimedia playback. I'd be first in line to snap it up!
 
This undermines the Ubuntu code about Ubuntu being free of charge. It seems to me (as I've always wondered this question myself) that since you pay for those other programs, like Windows or PowerDVD, that you are also paying for the rights of the software, and it is thus legal, right? So would it be illegal to, say, Wine a copy of a legally bought copy of PowerDVD or any other type of similar software?
 
EDIT: Ah, corporate greed. I'm in a little toss up myself at the moment. See, I bought a copy of Windows XP a few years ago for my old computer. Well, I built myself a new computer, formatted Ubuntu on the old one, and wanted to dual boot Ubuntu and XP on my new one. As it turns out, the cd keys that I BOUGHT are no longer valid, and they want me to buy new ones... Explain the legality of this? They are stealing from me are they not?

---

### Post by mazirian on 2006-11-09
That's an interesting question.  I just looked at a PowerDVD (v7) EULA, and it appears silent on that issue.  So emulation may well be an option for legal dvd playback for some users.  There may be some wrinkles in that analysis, but it certainly makes sense as you are using software you purchased for the purpose for which it was sold. Cyberlink at one point made a commercial version of PowerDVD for linux, though I don't think it is still available.  

Even if wine or some other emulator provides an answer of sorts, I still don't think that we should have to do any of this dancing around with licenses in order to play content we've already purchased the right to view.

---

### Post by Echo35 on 2006-11-09
> **mazirian said:**
> That's an interesting question.  I just looked at a PowerDVD (v7) EULA, and it appears silent on that issue.  So emulation may well be an option for legal dvd playback for some users.  There may be some wrinkles in that analysis, but it certainly makes sense as you are using software you purchased for the purpose for which it was sold. Cyberlink at one point made a commercial version of PowerDVD for linux, though I don't think it is still available.  

Even if wine or some other emulator provides an answer of sorts, I still don't think that we should have to do any of this dancing around with licenses in order to play content we've already purchased the right to view.

Agreed.

---

