---
title: "Are these issues solved with 9.04?"
date: 2009-02-26
forum: Mythbuntu
---

### Post by agamotto on 2009-02-26
Back in the day of 7.04 and 7.10, I could burn my shows to DVDs without any troubles whatsoever.  Since 8.04, this feature is useless.  Will this be fixed in 9.04?  If not, approximately when?  I know there are various fixes for some of these issues, but I am getting tired of patching things that used to work fine in OLDER versions.

Secondly, when is the analog port on the Hauppauge 1800 going to work without patches/fixes?  I have a 150 and an 1800 in my current system, and due to some conflict/issue with the two coexisting, I can't use the 150 now, as it doesn't record audio.  The digital part of the 1800 works fine.  I would be willing to pull the 150 out if the verdamt analog port on the 1800 worked.  Does anyone know if these will be fixed/addressed in 9.04, or is it time for me to find some other software to use as the base of my DVR?

---

### Post by agamotto on 2009-03-05
Sad, sad.  I have now tried MythDora and the LinHES version of Knoppmyth.  No go with either.  

MythDora seemed to be a winner, until it refused to connect to my router via wireless.  Hint:  It would help in the setup if you allow the user to set up the network LONG before they setup anything else.  The idea of using the MythWelcome bit would have been nice, but due to no network connection, I really couldn't get far in the configuration.  

LinHES also ran well, save for getting a black screen for Watch TV with either tuner card, and seemingly no way to drop out of the interface to go poking around, ala Mythbuntu.

Oh well, I guess I will just pack the thing away until I hear that something will work, as I am tired of being a beta tester.

---

### Post by theophile on 2009-03-05
Please contact our customer service department for a full refund.

---

### Post by Flecko on 2009-03-05
Excellent and supportive reply theophile. I'm sure it's people like you that keep the free software world a tightly knit community.

As for agamotto, I feel your pain. I've been using Mythbuntu since its first release, and I know what you're talking about. I'm currently experiencing the notorious "Channel Guide Slowdown" issue that's apparently been creeping around for awhile.

The truth of the matter is that there are always going to be bugs in free/open source software. Its a growing pain that will be us for a long time. For instance, the Linux kernel itself has that awful "iowait" bug thats been around for many versions.

The only thing I can tell you is search for a workaround until a real fix appears. What I end up doing is pausing my Live TV before I bring up the program guide unless I want Xorg to clobber my Mythfrontend and cause a freeze. It sucks, but unless anyone is willing to step up and get their hands dirty in the source, we just have to wait.

Don't give up hope!

PS - really theophile? pffft.

---

### Post by klc5555 on 2009-03-06
> **agamotto said:**
> Back in the day of 7.04 and 7.10, I could burn my shows to DVDs without any troubles whatsoever.  Since 8.04, this feature is useless.  Will this be fixed in 9.04?  If not, approximately when?  I know there are various fixes for some of these issues, but I am getting tired of patching things that used to work fine in OLDER versions.

Secondly, when is the analog port on the Hauppauge 1800 going to work without patches/fixes?  I have a 150 and an 1800 in my current system, and due to some conflict/issue with the two coexisting, I can't use the 150 now, as it doesn't record audio.  The digital part of the 1800 works fine.  I would be willing to pull the 150 out if the verdamt analog port on the 1800 worked.  Does anyone know if these will be fixed/addressed in 9.04, or is it time for me to find some other software to use as the base of my DVR?

If you find other DVR software for your Hauppauge 1800, it won't be Linux at all: the v4l driver does not yet support analog (analog support "coming very soon" since September 2007...) This is not specifically a 'buntu 9.04 issue (or Mythdora or Mythwhatever).

Problems with Mytharchive (and yes, they're legion, though fixes/workarounds do exist for most of them) pertain mostly to Mythtv 0.21 itself (except for some genisoimage, wodim, growisofs issues that are rooted in Debian silliness) Some of the continuing Mytharchive problems may continue to be fixed in Mythtv 0.21 and into Mythtv 0.22 ...but you'll likely need to ask at the source: the Mythtv list over at Gossamer Threads. 

But the question arises: if your DVR box ran right and archived right with Mythbuntu 7.x and Mythtv 0.20.2, why not continue to run Mythbuntu 7.x and Mythtv 0.20.2 on that machine? I had to move to Mythtv 0.21 (and its attendant problems) because of storage group support. But otherwise my master backend machine runs Mythbuntu 7.10, and since the mobo can't seem to handle the sound  changes in 8.x, it will continue to run Mythbuntu 7.10 until the day it dies (or until I need to convert it to ...um ..."MythSlack".)

So for your machine, unless there is a killer feature or support you deperately need in 8.x or 9.x (and Myth 0.21), wipe the machine and reinstall what actually worked for you: Mythbuntu 7.x with Mythtv 0.20.x. A working machine has to be better than putting it in the coat closet out of sheer frustration.

Just my $.02

Cheers! :)

---

### Post by theophile on 2009-03-06
> **Flecko said:**
> 
PS - really theophile? pffft.
The guy is complaining about having to lift a finger to get features he wants. He doesn't want to patch things, he just wants everything he wants out of the box. This thread isn't even asking for help, it's asking when someone is going to give him what he wants.

This isn't a commercial product. If you want support, ask for it and be willing to do a little work. Don't just complain that things don't automatically work. Or just get a TiVo.

---

### Post by Caps18 on 2009-03-06
> **Flecko said:**
> The truth of the matter is that there are always going to be bugs in free/open source software. Its a growing pain that will be us for a long time. For instance, the Linux kernel itself has that awful "iowait" bug thats been around for many versions.

The only thing I can tell you is search for a workaround until a real fix appears. What I end up doing is pausing my Live TV before I bring up the program guide unless I want Xorg to clobber my Mythfrontend and cause a freeze. It sucks, but unless anyone is willing to step up and get their hands dirty in the source, we just have to wait.

Don't give up hope!


Part of the problem is the development cycle timeline.  There are too many 'new' features added, without doing the boring troubleshooting and making all of the weird pieces of equipment work for everybody.

I think we should still be on 7.10, but working to make it a rock solid thing.  If I were to set it up at my parents house 300 miles away, I would want to know that it can work for years without any user induced problems.  But, I can't because a simple thing like filling up the partition with TV recordings causes it to stop working. 

Now, I haven't used 8.04, 8.10 or 9.04, so maybe these problems were fixed, but if there are new problems or bugs, I can't recommend it to non-Linux people.

---

### Post by Monsieur Gonzalez on 2009-03-07
Blame the right people. Blame Hauppauge people for not opening the specs for their cards, providing windows only drivers. Send them e-mails, tell them you use Linux and don't want to be treated like second class citizens. 

Keep in mind developers of Mythtv are doing it, as far as I know, for free, in the spirit of free software. 

Keep in mind that freedom seldom comes for free. You have to "fight" for it, in a way. 

Take a look at the success stories of other Mythtv users, and try to use that working hardware, and always check Linux compatibility of everything you buy.


Also, you might consider other options, even Windows based, why not?. 

Good luck.

---

### Post by Flecko on 2009-03-07
Despite the tone of agamotto's original post, (hey, everyone has a right to complain) he did ask clear questions. 

He wanted to know if DVD backup and his two tuners will work/be fixed in 9.04. So if anyone reading this is running 9.04 at this time with a similar setup, please post your experiences.

Lets all get along!

---

### Post by agamotto on 2009-03-09
> **theophile said:**
> Please contact our customer service department for a full refund.

Hahahahahaahaha!   I love people with a sense of humor.  I used to work in retail, so it was especially funny to me.

---

### Post by agamotto on 2009-03-09
> **klc5555 said:**
> 
But the question arises: if your DVR box ran right and archived right with Mythbuntu 7.x and Mythtv 0.20.2, why not continue to run Mythbuntu 7.x and Mythtv 0.20.2 on that machine? I had to move to Mythtv 0.21 (and its attendant problems) because of storage group support. But otherwise my master backend machine runs Mythbuntu 7.10, and since the mobo can't seem to handle the sound  changes in 8.x, it will continue to run Mythbuntu 7.10 until the day it dies (or until I need to convert it to ...um ..."MythSlack".)

Just my $.02

Cheers! :)

Thanks to a friend on another forum, I got my hands on a 7.10 iso, and have installed that as of yesterday.  So far, so good.  No sound issues, guide works, I will test the DVD burning once I have a few programs to put on a disc.  

I suppose the lesson I have learned from all of this is that I shouldn't bother upgrading anything until I HAVE to.  I just find it annoying to the extreme that an 'improvement' is quite worse than what it was intended to replace.  If I wanted that, I could use Vista!

---

### Post by agamotto on 2009-03-09
> **theophile said:**
> The guy is complaining about having to lift a finger to get features he wants. He doesn't want to patch things, he just wants everything he wants out of the box. This thread isn't even asking for help, it's asking when someone is going to give him what he wants.

This isn't a commercial product. If you want support, ask for it and be willing to do a little work. Don't just complain that things don't automatically work. Or just get a TiVo.

Actually, smarty-pants, I was complaining about things that STOPPED working after I did something called an UPGRADE.  Perhaps a review of the word upgrade in a dictionary would be of use.  

Having stepped off my soapbox, I did try several fixes that I found here and on other forums, to no avail.  Hence the 'it no workie!!!' whinging.
:)

---

### Post by dsbw on 2009-03-09
A critical rule of MythTV seems to be: Don't upgrade unless you absolutely have to. You'll read this over and over again, for precisely the reason you experienced. 

There are a lot of parts to the system. The odds of one of those parts being upgraded in a way that is upsetting to you is significant.

---

