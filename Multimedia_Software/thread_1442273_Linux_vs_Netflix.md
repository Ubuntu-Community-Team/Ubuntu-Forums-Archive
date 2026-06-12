---
title: "Linux vs Netflix"
date: 2010-03-29
forum: Multimedia Software
---

### Post by ArtemNY on 2010-03-29
It s#cks! It really s#cks! It made me so angry!

I'm a long time Netflix user. Watching movies right from my PC.
After switching to Linux I couldn't imagine that there could be such problem.

Opened Netflix. For a few minutes was choosing a movie. Clicked PLAY and.... BAAAM! Doesn't work.

Ok. Relax. Let's try to fix it (I said). It says that Nitflix supports by Windows and Mac only. Ignored that, tried to get some info from automated Netflix help machine.

After a few steps it said that I don't have a Silverlight. Opened MS to install a Silverlight. Installed it in a few secs. (It's actually called Moonlight for Linux).

Was just happy that the problem is fixed and I'll be able to watch my movies. But than, on the last page of installation Moonlight it said:
> 

        Netflix does not work with Moonlight at this time.  While Moonlight supports          all of the UI and media playback infrastructure, it lacks DRM support which          Netflix requires.  See this silverlight.net forum post and this page on the Moonlight wiki.
What the hell is this DRM (digital rights management)? How to fix it?

---

### Post by Wiebelhaus on 2010-03-29
You can't not right now , Netflix is scared your going to steal their crap so they enforce DRM , I personally don't use anything that uses DRM , period. And I won't , ever.

---

### Post by ArtemNY on 2010-03-29
> **Wiebelhaus said:**
> You can't
I HATE these two words! ](*,)

So there's NO chance to "play" Netflix in Linux not running a Virtual Machine? :(

---

### Post by mhpathfinder on 2010-03-30
No Netflix for Ubuntu or any other LINUX based operating system.  However, you can buy a ROKU box for $70, connect it to your TV and sound system and enjoy "Watch Instantly" Netflix, as well as having access to several other channels, besides Netflix, most of them at no additional charge beyond your low monthly Netflix fee.

Would it be nice to view Netflix on my Ubuntu Netbook Edition operating system?  Sure, but ROKU is a better alternative, viewing NETFLIX, many original independent films, listening to Pandora.com music, or exclusive web-based programs and presentations on a large TV screen with sound through my stereo system.

The ROKU box connects to your home network, either wired or wirelessly, then--with a code--identifies your queue for preferred channels, programs and movies and downloads the content to your ROKU box

I don't sell ROKU.  This is not a marketing message.  I just like it and think it's a better way to view "Watch Instantly" Netflix and other content.  And, no worry about your TV's operating system, neither Windows nor Mac, nor even LINUX, although I think the ROKU box is LINUX-based for its menus and channel selection software.

Alternatives are here, just not for viewing Netflix on a LINUX based computer.
:)

---

### Post by Naitsirhc Hsem on 2010-04-03
Why should you have to buy a separate piece of hardware to watch something you pay for anyway!!  Netflix should really offer a valid solution or people will keep trying to hack it and get around the DRM.

---

### Post by indylarry on 2010-04-03
I am sure that Netfix has to agree to use DRM if they want the content from the media companies. I don't blame them.  There seems to be a simple solution to this.  The ROKU box runs Linux.  That means the DRM code for Linux already exists.  I would be happy to pay $10-$20 for a proprietary app that would allow me to watch Netflix on Linux.  ROKU would gain another revenue stream to recover their development costs and Netflix would stop getting angry email from us *nixers.  Some will probably disagree, but I believe this would be a reasonable solution.

---

### Post by Naitsirhc Hsem on 2010-04-03
> **indylarry said:**
> I am sure that Netfix has to agree to use DRM if they want the content from the media companies. I don't blame them.  There seems to be a simple solution to this.  The ROKU box runs Linux.  That means the DRM code for Linux already exists.  I would be happy to pay $10-$20 for a proprietary app that would allow me to watch Netflix on Linux.  ROKU would gain another revenue stream to recover their development costs and Netflix would stop getting angry email from us *nixers.  Some will probably disagree, but I believe this would be a reasonable solution.

I don't disagree at all, that is an excellent idea!! Why haven't Netflix/ROKU/Microsoft thought of this.  It is a win win situation

---

### Post by snowpine on 2010-04-03
> **Naitsirhc Hsem said:**
> Why should you have to buy a separate piece of hardware to watch something you pay for anyway!!  Netflix should really offer a valid solution or people will keep trying to hack it and get around the DRM.

Sorry, you knew it wouldn't work in Linux when you paid for it. ;) Netflix's system requirements are clearly stated in the FAQ; they are not making any deceptive claims or misleading advertising IMHO.

---

### Post by Chronon on 2010-04-04
> **Naitsirhc Hsem said:**
> I don't disagree at all, that is an excellent idea!! Why haven't Netflix/ROKU/Microsoft thought of this.  It is a win win situation

I'm sure ROKU has signed a non-disclosure agreement and is not permitted to distribute the binary blobs, nor any information about them.  It's entirely up to Microsoft as to whether they will provide assistance to the Moonlight project (binary blobs).  Nobody else has any power to do anything about this.  The DRM is Microsoft's intellectual property.

---

### Post by conradin on 2010-04-04
Im pretty sure the means netflicks uses to monitor what OS youre using is via your browser headers. There are ways to change what your Computer shows up as to servers.  I cant recall right now what this is called. browser masquerading or something. Look into that.
[https://wiki.ubuntu.com/IceCat](https://wiki.ubuntu.com/IceCat)

---

### Post by Chronon on 2010-04-04
conradin: It doesn't matter if you trick Netflix's servers.  You will not be able to decrypt the streams.  You can already install Moonlight and launch the Netflix player.  However, you cannot (and will not be able to in the future) decrypt the media streams without help from Microsoft.

---

### Post by onecallednick on 2010-04-04
What about wine?  Anyone tried installing IE/firefox/chrome for windows and silverlight?  I haven't gotten it to work but I'm a n00b.

---

### Post by BobLand on 2010-04-04
I ran netflix via VirtualBox & FireFox for about 9 months.  Then they required Silverlight for the browsers.  I installed Moonlight.  Wouldn't work.  Installed Silverlight on IE.  Still wouldn't work.

Called Netflix and cancelled the account.  However, I really miss it.  They have movies that are not available anywhere else, both instant and DVD.

I've been thinking about the Roku box mostly because I'd rather watch movies on my 32" TV sitting on a cushy sofa.

---

### Post by princemanjee on 2010-05-20
> **conradin said:**
> Im pretty sure the means netflicks uses to monitor what OS youre using is via your browser headers. There are ways to change what your Computer shows up as to servers.  I cant recall right now what this is called. browser masquerading or something. Look into that.
[https://wiki.ubuntu.com/IceCat](https://wiki.ubuntu.com/IceCat)

I think you are referring to what is called a USER AGENT SWITCHER or spoofer. Essentially it will tell the web server you are accessing exactly what kind of OS and browser you are using, however the UAS will hijack those requests and fill in anything you choose. I have not seen one for Chrome (haven't looked either). The one for Mozilla works well but not for this purpose. Netflix will still attempt to look for WMP to play the content. If WMP can be ported over to linux - PROBLEM SOLVED. However it is not likely that anyone will do that.

Like Netflix HULU uses silver light and if you download moonlight that works fine on HULU for 99.9% of the media (there are exceptions as in olympic coverage and president obama's inauguration to name a few) that had some issues on linux machines because of DRM. Any DRM can be chosen however Netflix has cut a deal with Micro$haft in which M$ provides the DRM encoding software as required by the studios and in doing so M$ locks up its proprietary codec in windows machines along with all of netflix's customers. What I do not understand is if the codec was licensed for use on ROKU boxes and other set top hardware that will play netflix (Wii or other 3rd party players - not just M$ Xbox), why can it not be made available to the netflix clients by SOME means even a binary if an opensource client can not be made?

So far the VM is the only way I have gotten it to work and even that kinda sucks (even with 4GB of ram).

I wont buy a roku box cause that doesnt solve my problem, I already carry a laptop on the road I dont have room in my bag for an LCD and a roku box. The DVD by mail is useless if I am not home so... Streaming would be nice. However if I can't get it soon Netflix will quickly lose it's utility and be an expense I can do without.

---

### Post by Chronon on 2010-05-20
> **princemanjee said:**
> 
Like Netflix HULU uses silver light and if you download moonlight that works fine on HULU for 99.9% of the media (there are exceptions as in olympic coverage and president obama's inauguration to name a few) that had some issues on linux machines because of DRM. Any DRM can be chosen however Netflix has cut a deal with Micro$haft in which M$ provides the DRM encoding software as required by the studios and in doing so M$ locks up its proprietary codec in windows machines along with all of netflix's customers. What I do not understand is if the codec was licensed for use on ROKU boxes and other set top hardware that will play netflix (Wii or other 3rd party players - not just M$ Xbox), why can it not be made available to the netflix clients by SOME means even a binary if an opensource client can not be made?

Hulu uses flash, not Silverlight.  I watch Hulu routinely and don't have Moonlight installed.

---

### Post by happymellon on 2010-05-23
So I have a question about all of this. If Silverlight is required for all streaming, how is it playing on the PS3, Wii, iPhone/iPad?

The PS3 implementation, AFAIK, is Blu-ray Java based, it cannot be Silverlight due to being Cell based. The iPhone/iPad doesn't support Flash, so I doubt it would support Silverlight out of principal.

Is there a modified JVM to run blu-ray Java on Linux? Does anyone have an iPad so we can see how it connects and streams to netflix?

---

### Post by Stray Wolf on 2010-05-23
I would think that people willing to pay for viewing content in a digital environment where that isn't necessary shows responsibility on the part of us consumers.  We know we'd be shooting ourselves in the foot by downloading torrents of media for free.  But unfortunately, that's what I end up doing.  If a Linux users money isn't good enough then media barons shouldn't pitch a fit when I have to find creative ways to get the same content other OS users get.

---

### Post by akbeancounter on 2010-05-24
> **Stray Wolf said:**
> We know we'd be shooting ourselves in the foot by downloading torrents of media for free.  But unfortunately, that's what I end up doing.  If a Linux users money isn't good enough then media barons shouldn't pitch a fit when I have to find creative ways to get the same content other OS users get.

It's not as if circumventing the law is your only option.  I have yet to come across anything on Netflix that was *only* available in streaming format.  If you want to watch the movie, you have several legal avenues that don't require you to run a commercial OS: Buy a DVD, rent a DVD, or get a compatible device (Roku, gaming consoles, newer TiVos, and certain brands of TV or Blu-Ray player.)

Yes, these options cost money, but that's life.  Mac OS users are quite accustomed to being last in line, if they're included at all, but they acknowledge their choice to use a minority OS, and that doing so involves some trade-offs.

---

### Post by perspectoff on 2010-05-25
> **Wiebelhaus said:**
> You can't not right now , Netflix is scared your going to steal their crap so they enforce DRM , I personally don't use anything that uses DRM , period. And I won't , ever.

Don't get your knickers in a bunch.

The way Netflix delivers its streaming content to the Wii is by distributing a CD-ROM that runs in the Wii. All the DRM modules are on the CD.

There is no reason Netflix could not do the same thing for Linux users. It took them a while to come up with the Wii solution (which works great, by the way), so give them a little more time to come up with a system for Linux that is similar.

Netflix licenses the Microsoft DRM technologies, I believe, and Microsoft would love to have its DRM technologies pervade the Linux world.

While I'm an avid open source advocate, there is nothing wrong with DRM add-ons on a CD, in order to use specific services.

Moonlight (2.99) did pretty well for me during the Olympics -- the restrictions were not based on the operating system but were imposed on an ISP-basis (blackouts were imposed unless you were a subscriber of a service that contracted for coverage).

---

### Post by perspectoff on 2010-06-04
> **mhpathfinder said:**
> No Netflix for Ubuntu or any other LINUX based operating system.  However, you can buy a ROKU box for $70, connect it to your TV and sound system and enjoy "Watch Instantly" Netflix, as well as having access to several other channels, besides Netflix, most of them at no additional charge beyond your low monthly Netflix fee.

Would it be nice to view Netflix on my Ubuntu Netbook Edition operating system?  Sure, but ROKU is a better alternative, viewing NETFLIX, many original independent films, listening to Pandora.com music, or exclusive web-based programs and presentations on a large TV screen with sound through my stereo system.

The ROKU box connects to your home network, either wired or wirelessly, then--with a code--identifies your queue for preferred channels, programs and movies and downloads the content to your ROKU box

I don't sell ROKU.  This is not a marketing message.  I just like it and think it's a better way to view "Watch Instantly" Netflix and other content.  And, no worry about your TV's operating system, neither Windows nor Mac, nor even LINUX, although I think the ROKU box is LINUX-based for its menus and channel selection software.

Alternatives are here, just not for viewing Netflix on a LINUX based computer.
:)

Roku is already Linux based and is not portable (and therefore not better).

Netflix distributes DRM components on CD-ROM for Wii users. It could easily do the same thing for Linux users.

Just keep sending them requests to do so.

---

### Post by left 4 shred on 2010-06-05
> **happymellon said:**
> So I have a question about all of this. If Silverlight is required for all streaming, how is it playing on the PS3, Wii, iPhone/iPad?

The PS3 implementation, AFAIK, is Blu-ray Java based, it cannot be Silverlight due to being Cell based. The iPhone/iPad doesn't support Flash, so I doubt it would support Silverlight out of principal.

Is there a modified JVM to run blu-ray Java on Linux? Does anyone have an iPad so we can see how it connects and streams to netflix?

I'm pretty sure this is why it works on these systems:

1. PS3 and Wii requires a Disk to be able to stream the video. The Disk contains everything it needs to run it so I'm sure there's a port of Silverlight for the PS3/Wii (I heard something about the PS3 might be getting a firmware update late this year that offers stream instantly from the system without need of a disk).

2. Considering that Netflix can be natively watched on Macs now, it does makes kinda since that the iPhone/iPad can stream them. Whether or not if they support flash they're made to be "state of the art" portable multimedia devices so I'm sure they would have silverlight or some special version compatible with the device to run them.

I don't know anyone with an iPad or the money to spare on that digital clipboard. :P If I find anything out about it I'll try to remember to bring it here. 

Sadly I think it will be a long time before we get Netflix on Linux, if we ever do. Xbox getting it was a no brainer. Microsoft owns Xbox and the DRM so naturally they'll put a convenient App on their system to try to attract more people to the system. Also Apple is has been booming in the last few years since their computers became "unmatched god-sent computers" and even with the whole Mac vs Pc hooplah, opening the DRM usage to Apple must have helped them make a lot of money due to Apple only houses. Same goes with the Wii, huge market with older folks (not saying younger people don't partake, I have one and mainly use it for Netflix, lol.) The Wii was a huge hit for a lot of people with it's family rated fun games. Now it has family fun videos for a low monthly rate. Copy and paste what I just said about the Wii but put it for PS3 and change the obvious.  

Linux might be a lot of our worlds in terms of computing but we still have to face up to the fact that we are the minority. Luckily we can solve a lot of incompatibility issues with virtual machines and wine. (I have heard of people getting it to work both horribly and very well in sun virtualbox, I've not tested it myself but i'm about to once I reinstall virutalbox). But the sad part is that we pretty much have to bend over and take it right now. I was thrilled about Guitar Pro 6 having a Linux version...but it was soon depressed once I realized it didn't support 64bit. 

Summary, sadly I believe that it goes where they'll make more money. I'm sure Netflix wants to release a Linux version, but the beef we should have is with M$. They hold the rights to the DRM and where it goes. 

Try writing a letter to Microsoft (assuming that it will matter)

[http://www.petitiononline.com/Linflix/](http://www.petitiononline.com/Linflix/) Sign this petition (assuming that it will matter)

Enough bulk will bring even the fattest cow down, I just don't know if we're the if we're enough bulk.

---

### Post by left 4 shred on 2010-06-05
> **perspectoff said:**
> Don't get your knickers in a bunch.

The way Netflix delivers its streaming content to the Wii is by distributing a CD-ROM that runs in the Wii. All the DRM modules are on the CD.

There is no reason Netflix could not do the same thing for Linux users. It took them a while to come up with the Wii solution (which works great, by the way), so give them a little more time to come up with a system for Linux that is similar.

Netflix licenses the Microsoft DRM technologies, I believe, and Microsoft would love to have its DRM technologies pervade the Linux world.

While I'm an avid open source advocate, there is nothing wrong with DRM add-ons on a CD, in order to use specific services.

Moonlight (2.99) did pretty well for me during the Olympics -- the restrictions were not based on the operating system but were imposed on an ISP-basis (blackouts were imposed unless you were a subscriber of a service that contracted for coverage).

I like this idea but I don't love it. It would definitely at least be a start to something good in our direction. Either way it wouldn't help me unless I ripped the CD on my desktop and put it on my netbook and mounted it. I wouldn't want to have to buy an external DVD drive just to watch netflix in bed.

---

### Post by cjpetrie on 2010-06-05
One good reason for wanting not to need separate box and a TV is that Netflix streaming offers a good alternative to airline movies on long flights that have WiFi. If you aren't running Linux. :(

---

### Post by Kamron42 on 2010-06-11
Hey all,

Here is a petition page on facebook to get netflix support for linux.  [http://www.facebook.com/pages/Bring-Netflix-To-Linux/128791593812850](http://www.facebook.com/pages/Bring-Netflix-To-Linux/128791593812850)
We need to show numbers to them.  It's been up 5 days and has 277 members, we need a lot more.  Please check out the page and click "like" to show support, and spread the word as best you can.  

Thanks,
Kamron

---

### Post by naknak987 on 2010-06-12
I clicked like to show my support, also sent it to everyone in my friends list. Most of them will be like, "whats linux?"

---

### Post by JEDIDIAH on 2010-07-01
> **cjpetrie said:**
> One good reason for wanting not to need separate box and a TV is that Netflix streaming offers a good alternative to airline movies on long flights that have WiFi. If you aren't running Linux. :(

A Netflix player that supports a real media remote would also be a nice plus. The remotes on those Roku boxes is a crippled joke. It's much like an AppleTV remote.

While shelling out for a single Roku box isn't bad, I don't just have one TV. Plus I run MythTV on my desktop machine too.

A closed binary would still allow Netflix to be in control and subject us to all of the DRM nonsense and make all of the content providers happy.

---

### Post by artcarney on 2010-07-11
Why is this topic marked "SOLVED"?

---

### Post by Cavin on 2010-07-12
> **artcarney said:**
> Why is this topic marked "SOLVED"?
[COLOR="White"]y[/COLOR]

---

### Post by raldz on 2010-07-13
I've been using Ubuntu since 4.10 or 5.04.. and Netflix is the only reason I use Windows now... very inconvenient as I have to dual boot just to watch Netflix... and no, I don't like the quality when using a virtual machine.. all the HTPC that I built for friends are dual boot just because of Netflix.. I "liked" the facebook page for this petition..

---

### Post by parker.casey@gmail.com on 2010-07-15
> **Wiebelhaus said:**
> You can't not right now , Netflix is scared your going to steal their crap so they enforce DRM , I personally don't use anything that uses DRM , period. And I won't , ever.

Netflix isn't scared at all. The people who supply netflix with their media on the other hand, are.

---

### Post by yippy on 2010-07-22
> **artcarney said:**
> Why is this topic marked "SOLVED"?
???

---

### Post by djupp on 2010-08-11
> **cjpetrie said:**
> One good reason for wanting not to need separate box and a TV is that Netflix streaming offers a good alternative to airline movies on long flights that have WiFi. If you aren't running Linux. :(

Running the risk of updigging this thread, but what airline are you flying with? Streaming movies on an airplane sounds way too much science fictionesque to me :D

On the thread being marked as solved I guess the answer is easy: Not gonna happen, "solved"... Unless of course NetFlix and MS get their **** together

---

### Post by omskates on 2010-08-13
You don't even get full access to netflix streaming through the Wii.  You get a "special" list which excludes much of the movies which would be available through a windows os.

---

### Post by oldsoundguy on 2010-08-13
Actually, several Blu-Ray player manufacturers now offer net enabled (hard wired or WiFi) devices that will stream ALL of the Netflix content (including 3D).  I have a Sony unit that works fine .. and they are about to add Hulu into the sources list.  No more having to rely on a funky Windows computer to download and having it crash in the middle of the movie.
(Sony OS is Java.)
It is SO much better and faster than trying to use a computer and then stream it to the set. 
Now, IF you have to have that content on your laptop, getting the providers such a Netflix to write their proprietary programs for Linux may be a VERY long wait.  With less than 2% of the total market using Linux at present, not a big enough market for them to consider.  PLUS Linux changes it's kernel too often for 3rd party providers to bother to keep up if there is no real BUCKS in it for them!

---

### Post by khuffmanjr on 2010-08-23
> **oldsoundguy said:**
> 
Now, IF you have to have that content on your laptop, getting the providers such a Netflix to write their proprietary programs for Linux may be a VERY long wait.  With less than 2% of the total market using Linux at present, not a big enough market for them to consider.  PLUS Linux changes it's kernel too often for 3rd party providers to bother to keep up if there is no real BUCKS in it for them!

2% is potentially a lot of revenue for Netflix.  2% of 100 people is 2 people, or in other words, not a lot.  At $9 a month Netflix only gets $216/yr.  But, lets say that Netflix could reel in another 20,000 subscribers by streaming to GNU/Linux users, then they'd be getting another $2.16 million per year.  Certainly worth the time and money, imo.

---

### Post by crohakon on 2010-09-03
> **snowpine said:**
> Sorry, you knew it wouldn't work in Linux when you paid for it. ;) Netflix's system requirements are clearly stated in the FAQ; they are not making any deceptive claims or misleading advertising IMHO.

Actually, at one time netflix streaming did work in Linux. Back when netflix was not using Microsoft's silverlight. And even now it does not say "Microsoft Windows or Mac" it says "PC or Mac".. or at least it did last I looked a few months ago.

But I agree, at this point netflix does not get my cash. But I would gladly pay for it should they give me the option.

---

### Post by yevgeni on 2010-09-03
Sometimes us Linux users are too nice and try too hard to play by the rules...

I'm sure we can all agree here that all ANY form of DRM accomplishes is losing revenue for the companies that employ it. Think about it... There is no proprietary software that hasn't been hacked when the need has been sufficient. So the bigger and more complex (therefore more expensively) they build these DRM's, the more they stand to lose when these technologies fall. I think we OWE it to ourselves and computing as a whole to promote open source compatibility by actively attacking these technologies by reverse engineering, hacking, and cracking the binaries. After all, the binaries themselves are nothing but machine code, and machine code is nothing but very abstract source code, if you can follow it.

I for one am currently researching very thoroughly how the MS plugin handles Netflix's streaming video. It's just a binary program sitting on my computer that takes illegible data, performs some "magic" on it, and out pops video. I can analyze what comes in and what goes into my video memory for playback. Knowing what I know about cryptography, I'll say that brute forcing the crypto is impractical, but have been trying to come up with a framework for a possible plaintext attack on the encrypted data stream. I have written several small helper programs that allow me to iterate through captured data to try to find patterns, correlations, etc. I'm by no means saying I'm a hacker, but I understand cryptography, and above all that computers are just adding machines that deal with 1's and 0's, and where there's a will, there's a way. 

Of course, were I to crack the DRM, I'd share my spoils with all of the internet.

---

### Post by zoidburg016 on 2010-09-13
> **yevgeni said:**
> Sometimes us Linux users are too nice and try too hard to play by the rules...

I'm sure we can all agree here that all ANY form of DRM accomplishes is losing revenue for the companies that employ it. Think about it... There is no proprietary software that hasn't been hacked when the need has been sufficient. So the bigger and more complex (therefore more expensively) they build these DRM's, the more they stand to lose when these technologies fall. I think we OWE it to ourselves and computing as a whole to promote open source compatibility by actively attacking these technologies by reverse engineering, hacking, and cracking the binaries. After all, the binaries themselves are nothing but machine code, and machine code is nothing but very abstract source code, if you can follow it.

I for one am currently researching very thoroughly how the MS plugin handles Netflix's streaming video. It's just a binary program sitting on my computer that takes illegible data, performs some "magic" on it, and out pops video. I can analyze what comes in and what goes into my video memory for playback. Knowing what I know about cryptography, I'll say that brute forcing the crypto is impractical, but have been trying to come up with a framework for a possible plaintext attack on the encrypted data stream. I have written several small helper programs that allow me to iterate through captured data to try to find patterns, correlations, etc. I'm by no means saying I'm a hacker, but I understand cryptography, and above all that computers are just adding machines that deal with 1's and 0's, and where there's a will, there's a way. 

Of course, were I to crack the DRM, I'd share my spoils with all of the internet.

Why not have the internet assist you? Create an application that captures the data and uploads it to a database. People using dual boot systems can run it while they're streaming from netflix. With more data you have more of a chance of cracking it.

---

### Post by Perkins on 2010-09-13
My younger brother is currently experimenting with installing silverlight into the windows version of firefox in Wine.  It mostly works, but has some stability issues and random crashes that he hasn't managed to iron out yet.  I will ask him if he's made any progress when next I speak to him.


I'm not sure what the movie industry is thinking with DRM...  If you can play it, you can pirate it.  Period.  Worst case involves a video camera.  They are wasting their time and their money on it.

---

### Post by archeryrob on 2010-09-13
I tired the virtual machine with windows installed in it and was completely unhappy with that. XP would not set to a screen resolution I was happy with on my wide screen TV. It was like watching a full screen movie on a wide screen TV and in a box too, 

Really hated controlling the computer in the Vmachine, felt like using a 10 year old computer

---

### Post by bobglaub on 2010-09-15
I just wanted to add my .02 cents.

I think it's funny that people think everything can be hacked and that it's just so easy to do, when netflix has stopped us linux users for quite a while now from successfully watching streaming movies and what-not.  I for one, have canceled my netflix subscription due to lack of netflix support.  i will continue to find ways to watch the movies and shows I want, whether they be by legal means or not.

I often find myself stranded at various airports for hours at a time, and it would be oh so nice if I were able to log into a netflix account and watch a movie to help pass the time, but alas, such is not the case.  the virtual machine route will nto work for me as i have a netbook.  And so, i find myself hitting up the old sites that haven't let me down for years, the torrents.  Hulu does work, but there is only so much on hulu.  And so it goes, another 18 hour layover, with no movies to watch.  browse the internet, chat on facebook with old friends, and read forums regarding people hacking silverlight DRM.  which from the looks of it, may never happen.

to the guy that said he'd have to rip a CD containing the DRM, then mount it virtually on his netbook, that is EXACTLY the reason why they won't release the disc.  people would just download it from a torrent site.  I agree, my netbook wouldn't allow me to use a disc either, so perhaps they could release a coded USB pen drive that has to connect to their site, and it's registered with your account.  I think a lot of netbook users use linux because Windows will kick your netbook's a$$.  at idle, with windows 7 starter (it's what this netbook came with) windows used up 70% of my ram.  just to sit there.  it was pathetic.  the only reason I still have windows 7 on my desktop at home is so I can run Flight Simulator X.  Eventually, once x-plane catches up to fsx, i'll switch over to that software completely, and i'll never have to use windows again.  unless I want to watch a netflix movie.  ;)

---

### Post by Perkins on 2010-09-16
Just talked to my brother.  You can get the Netflix version of silverlight to run in wine along with the windows version of firefox, and it will play most things, but not Netflix.  He thinks there's some part of the DRM code that doesn't quite run right yet.

I'm not sure what they're hoping to accomplish with their DRM...  I mean, what's to prevent me from plugging the video out on my computer into the video in on my VCR and making as many copies as I like?...

---

### Post by oldsoundguy on 2010-09-16
Streaming is one thing .. they can and should correct that just because Windows itself is slowly losing market share (another 1 1/2% lost world wide this month according to W3C)(Most going to Apple because of laptop sales for back to school)(Apple has over 50% of the US university laptop sales)

They have already blown it on their mail service.  My brother has been a member for several years and still has disks delivered.  Used to be OCCASIONALLY one would not work in his stand alone player .. now it is OCCASIONALLY one WORKS in his player. 
He winds up returning more than he watches.

Netflix grew too fast too quickly and lost their view  of quality control and the fact that they provide a SERVICE that CAN be replaced by someone else .. simply because they can not hold a PATENT on their implementation of OTHER'S ideas ...  which is the foundation of their business plan ... they just did it FIRST.

"On Demand" may be their competition eventually for streaming content as their libraries expand.

---

### Post by Moonf4 on 2010-09-16
I used to work for a video encryption company. The Movie Studios are the one who dictate that content protection methods have to be used. I would say it is a safe bet that Netflix has no choice or option in the matter. My old companies customers were ISP's and telco's around the globe. If they wanted to offer their customers Pay per view movies, the movie studios would say fine, you go out and buy and implement one of these DRM solutions and we will provide you the feeds with our content. No DRM, no content. 

I would imagine it is the same for Netflix. The movie studios most likely dictated that they can stream to PC and MAC and any hardware vendor that implements DRM into their device, but not to any open linux platform. As several people have seen, most of the HD media players run linux, but it is not an open version that any home owner can mess around with, so it is not a linux issue preventing a linux netflix client. They just can't offer it.

---

### Post by glave on 2010-09-17
> **Moonf4 said:**
> I used to work for a video encryption company. The Movie Studios are the one who dictate that content protection methods have to be used. I would say it is a safe bet that Netflix has no choice or option in the matter. My old companies customers were ISP's and telco's around the globe. If they wanted to offer their customers Pay per view movies, the movie studios would say fine, you go out and buy and implement one of these DRM solutions and we will provide you the feeds with our content. No DRM, no content. 

I would imagine it is the same for Netflix. The movie studios most likely dictated that they can stream to PC and MAC and any hardware vendor that implements DRM into their device, but not to any open linux platform. As several people have seen, most of the HD media players run linux, but it is not an open version that any home owner can mess around with, so it is not a linux issue preventing a linux netflix client. They just can't offer it.

This is what people truely fail to realize. DRM isn't about protecting the content AT ALL. DRM is just another outlet for the industry to make money. They make their content outlets use DRM, so the DRM has to be licensed from approved solutions, which the entertainment industry also has vested interests in. The industry itself doesn't think DRM is protecting anything, as you can already download 99.9% of what is out there already. It's all about filling their pockets at the expense of the honest customers.

---

### Post by mojotexas on 2010-09-19
Why is this thread marked as SOLVED when it should maybe be marked UNSOLVEABLE?

---

### Post by Shibblet on 2010-09-20
I recently signed up for NetFlix.  It comes built in to my new Blu-Ray player from LG.  Great feature too.  Streaming content is really nice.

I also have a friend who has a PS3, and he has a NetFlix Disc that is loaded in the PS3 to allow him to stream movies to his console.  There is also a disc for the Wii.  Both of these discs are provided with your NetFlix subscription.  

You do not need a disc to use NetFlix on the Blu-Ray players, the ROKU, any NetFlix ready device... and the XBox 360.  Apparently "Silverlight" is built into the XBox and DRM as well.

So... if you have DRM in your XBox, you have a disc that allows playback on PS3 and Wii, you have DRM built into the "NetFlix Ready" devices, why the heck can't you have a Linux App that has DRM built in for Linux users?

Seems reasonable to me.  People don't want to skirt the DRM, they just want to use the streaming service.  I mean, really!  $8.99 a month is an AWESOME price to allow people to stream all of the movies and TV shows that they want.  Linux users want that too.

NetFlix needs to make an app.

---

### Post by Perkins on 2010-09-20
> **Shibblet said:**
> 
So... if you have DRM in your XBox, you have a disc that allows playback on PS3 and Wii, you have DRM built into the "NetFlix Ready" devices, why the heck can't you have a Linux App that has DRM built in for Linux users?



Reed Hastings is on the Micro$oft board of directors and has been quoted as saying that it's amazing to work with them and see the strategies that have made their company so successful.  Need I say more?

---

### Post by sheena2010 on 2010-09-22
I am sure that Netfix has to agree to use DRM if they want the content from the media companies. I don't blame them. There seems to be a simple solution to this. The ROKU box runs Linux. That means the DRM code for Linux already exists. I would be happy to pay $10-$20 for a proprietary app that would allow me to watch Netflix on Linux.



[advertising](http://www.worldpixelmile.com)

---

### Post by dhughes on 2010-09-23
> **mojotexas said:**
> Why is this thread marked as SOLVED when it should maybe be marked UNSOLVEABLE?

 Exactly! 

 I Googled 'Netflix and Linux' saw this thread and [SOLVED] in the search results, sifted through five pages of comments only find it's all been a waste of my time.

---

### Post by snowpine on 2010-09-23
> **dhughes said:**
> Exactly! 

 I Googled 'Netflix and Linux' saw this thread and [SOLVED] in the search results, sifted through five pages of comments only find it's all been a waste of my time.

You could have saved yourself a lot of time by visiting the netflix.com FAQ's:]

> What are the system requirements to watch movies instantly on my PC or Mac?

You must have a computer running Windows or Mac OS X and an active broadband connection to the Internet. 

---

### Post by Perkins on 2010-09-23
>  You could have saved yourself a lot of time by visiting the netflix.com FAQ's:] By that token, attempting to run Quickbooks, Oblivion, Halo, M$ Money, or any number of other things is obviously a complete waste of time.  The fact that it's not on the list of supported operating systems doesn't necessarily mean it won't work, just that the company doesn't test and support it.

---

### Post by snowpine on 2010-09-23
> **Perkins said:**
> By that token, attempting to run Quickbooks, Oblivion, Halo, M$ Money, or any number of other things is obviously a complete waste of time.  The fact that it's not on the list of supported operating systems doesn't necessarily mean it won't work, just that the company doesn't test and support it.

Please share your secret method then, because there are lot of people eager to learn how. :)

---

### Post by Perkins on 2010-09-24
Netflix doesn't quite work.  My point was that there's a lot of programs that say "windows" in the system requirements, but will run on Linux anyway.  So their FAQ saying windows doesn't mean it's not worth looking at.  This thread should probably be marked as unsolved for the time being.

My next area of experimentation is with ReactOS.  The open source windows clone.  It's not quite stable enough at the moment yet though.  The figure about another year before it hits beta.

---

### Post by grygub on 2010-09-30
At the moment I stream netflix through my xbox. Netflix streaming on the xbox requires you to have an xbox live subscription which is another $10 a month. I don't plan to renew this when it runs out.

I do have a suggestion for a solution though. Its known that netflix is currently working on an android app. Being that android is an open and understood operating system could the smart ones out there emulate the android os and play me some netflix!

---

### Post by Perkins on 2010-10-01
[http://developer.android.com/guide/developing/tools/emulator.html](http://developer.android.com/guide/developing/tools/emulator.html)

This what you're looking for maybe?  ;)

---

### Post by grygub on 2010-10-03
Nice now we just need to wait for the app to be released!

---

### Post by oregonbob on 2010-10-03
Netflix uses and requires Microsoft Silverlight to run. Until there is a linux port the best you can do is install virtualbox and a Windows XP virtual machine. I do it this way and have it working acceptable. When I tried a Windows 7 virtual machine the sound and video was always choppy and could not find it resolved.

It really sucks not being able to run Netflix on native linux. I've heard the easiest solution is to purchase one of those little $70 Roku boxes that allows Netflix on any computer. It is called Roku. If your time is worth $5/hour, the little black box is best.

---

### Post by lordawesome on 2010-10-05
sudo apt-get me a sandwich

I tried this code, but netflix still doesn't work.. Any ideas???

---

### Post by giraffedata on 2010-10-06
> **glave said:**
> This is what people truely fail to realize. DRM isn't about protecting the content AT ALL. DRM is just another outlet for the industry to make money. They make their content outlets use DRM, so the DRM has to be licensed from approved solutions, which the entertainment industry also has vested interests in. The industry itself doesn't think DRM is protecting anything, as you can already download 99.9% of what is out there already. It's all about filling their pockets at the expense of the honest customers.

That would be a pretty dumb way for a copyright owner to make money, as it wastes all the labor and other resources (= money) to engineer, distribute, and administer DRM things.  If people are willing to pay for DRM tools to watch a movie, they're willing to pay the movie studio directly to watch it, so the studio could make way more money just by raising its prices.

So it must be that the folks who own movie copyrights actually believe they're selling more copies because DRM frustrates people's attempts to redistribute the movies.  Incidentally, in the US, DRM frustrates one's ability to make a copy even if it's technically easy to break the DRM, because of the law against breaking DRM (separate from the law against making the copies).

---

### Post by giraffedata on 2010-10-06
I think there's a reason no one has mentioned that copyright owners would be willing to provide software for Wiis, Rokus, and Windows machines to watch their movies but not willing to provide software for Ubuntu-like systems:  Linux is open enough that even without source code to the decryption piece, it would probably be easy to capture the output and make a perfect digital copy.  Which you could then pass on to others in lieu of their paying to see it.  On an appliance like a Roku, I'm sure that's impractical, and on a Windows machine, with the entire operating system being secret and unmodifiable, it's probably also hard to do that.

---

### Post by Perkins on 2010-10-07
> **giraffedata said:**
> So it must be that the folks who own movie copyrights actually believe they're selling more copies because DRM frustrates people's attempts to redistribute the movies.


Except that the DRM patent royalty fees aren't paid directly by the end user.  They are paid by application developers who wish to support it.  Every time you buy a copy of Windows or OS X, or whatever DRM-equipped media player you happen to like, you are paying the recording industries up front for the possibility that you might want to watch some of their protected content.

GNU software projects, being free, generally have a difficult time obtaining the funding to purchase patent licenses.  Netflix, having close ties to Microsoft, really wouldn't want them to do so anyway.

---

### Post by Perkins on 2010-10-07
> **giraffedata said:**
> Linux is open enough that even without source code to the decryption piece, it would probably be easy to capture the output and make a perfect digital copy. 

Yes, it is.  Gstreamer can do it.

> **giraffedata said:**
> On an appliance like a Roku, I'm sure that's impractical

Nope.  Plug your device's outputs into your VCR or DVR's inputs and make all the copies you like.  Any Macrovision(tm) protection can be stripped with a filter box available at the local Radio Shack.

> **giraffedata said:**
>  and on a Windows machine, with the entire operating system being secret and unmodifiable, it's probably also hard to do that.

Microsoft has made that claim as part of their attempt to lock Linux out of the digital media market.  It is false.  There are a number of programs capable of recording directly off the screen and audio outputs.  Furthermore, even if they somehow managed to disable those, it's still completely vulnerable to hooking your machine up to a recorder device as explained above.  Cables for doing so can usually be found relatively cheaply.


If you can play it, you can pirate it.  Period.

---

### Post by evPaseo on 2010-10-12
Just got off the phone with Netflix support.  It sounds like the only way to get Netflix IT working on a Linux player is to flood their customer support lines with requests.  I doubt even that would yield the result we're all looking for, but wouldn't it be better to voice our collective displeasure to their customer support rather than complain to each other about it here. You can reach their customer support by calling: 1-866-716-0414.  Please be kind but firm that a growing Linux community is looking for Netflix to step-up and provide support for our operating system.

---

### Post by rotorbudd on 2010-10-13
> **lordawesome said:**
> sudo apt-get me a sandwich

I tried this code, but netflix still doesn't work.. Any ideas???

Try:  apt-get me a beer
Worked for me

---

### Post by segallis on 2010-10-14
I'm guessing it only a matter of time before frustration and inconvenience leads a few creative and technically able individuals to solve this problem outside of the MS/Netflix/Hollywood families.

While I have no personal interest in pirating content, I do expect to be able to watch free content and content that I pay for on the HW that I choose; and to be able to time shift it if I choose; and to be able to buffer as much content as I choose to avoid choppy playback due to overloaded servers, ISPs or slow DL speeds.

If a windows box can be made to send and receive the proper data to any provider, then a linux box can be made to do so.

I suspect that DRM currently enjoys some measure of success for lessening the extent of piracy - in some cases only in quality rather than quantity.  DRM will die when its cost (measured in money/effort/reduced market share) exceeds it benefit.  Its end is inevitable (remember the history surrounding CDs 30 years ago).

Eventually, someone will simply write a graphics card driver (or possibly it already exists) whose sole purpose is to accept digital video and then to re-encode it in whatever format the user specifies (like a pipe to ffmpeg, or something similar), via a dvr-like control gui.  Then there will exist a single capture utility - for ANY OS - that will allow virtually lossless capture of any format video, from any player imaginable.

Then those of us who pay for content will have the freedom to time shift programs and overcome connection bottleneck problems.  And the industry monopolies will move from DRM as a means of maintaining their sales, to competetive pricing and innovative services in order to make piracy less attractive.

---

### Post by perspectoff on 2010-10-14
> **omskates said:**
> You don't even get full access to netflix streaming through the Wii.  You get a "special" list which excludes much of the movies which would be available through a windows os.

That's not true. You can select any movie available for streaming and add it to your favorites, then watch it from the Wii.

You just haven't learned how to do it, yet.

The previous poster who said that content suppliers to Netflix are the ones that are nervous is spot on.

That is the reason that many studios don't license their movies for streaming in the first place. 

But it is all pretty stupid. Any streaming video can be recorded in Windows as it is, and there are lots of Windows applications available to copy Netflix DVD disks, apparently. There is no copy protection scheme that hasn't been broken. heck, the Chinese have even copied the Windows OS, not to mention nearly every movie released.

Worrying that the same thing will happen in Linux is ridiculous -- the cow has long left the barn. 

The question may be really whether Microsoft (and Apple and Roku and other services) pay a form of kickback to Netflix to provide Netflix services through their platforms.

It is unlikely that Netflix would receive kickbacks from the Linux community, and in business that is often the bottom line.

Technology hurdles? Nope. User base too small? Nope. Money? Yep.

---

### Post by ebozzz on 2010-10-20
[http://blogs.techrepublic.com.com/opensource/?p=1745](http://blogs.techrepublic.com.com/opensource/?p=1745)

---

### Post by tbug on 2010-10-21
I just read this entire thread in hopes of figuring it out.

Guess it's time to sit back and see what happens.

:popcorn:

---

### Post by MunchySnacks on 2010-10-23
Why the heck is this marked as Solved when it is obviously not.....?

---

### Post by Old *ix Geek on 2010-10-23
> **MunchySnacks said:**
> Why the heck is this marked as Solved when it is obviously not.....?I was wondering that, too. :confused:

Anyway, it pisses me off when companies--such as Netflix--that run their businesses on Linux, refuse to support Linux for its customers. Somehow, that just doesn't make sense.

---

### Post by chizzad on 2010-10-23
Has anybody tried to run the Roku os in virtualbox? if that could be made to work it might just offer an acceptable solution :guitar:

---

### Post by chizzad on 2010-10-23
or try to reverse engineer the drm codes from the discs for the Wii or Ps3.

---

### Post by macem29 on 2010-10-23
> **Perkins said:**
> snip........

I'm not sure what they're hoping to accomplish with their DRM...  I mean, what's to prevent me from plugging the video out on my computer into the video in on my VCR and making as many copies as I like?...

I'm pretty sure all concerned parties would consider that activity a huge victory

---

### Post by Perkins on 2010-10-24
I suppose I could use a DVD recorder instead...  Probably cheaper than buying tapes at this point anyway...

---

### Post by BumberBot3K on 2010-10-24
> **ebozzz said:**
> [http://blogs.techrepublic.com.com/opensource/?p=1745](http://blogs.techrepublic.com.com/opensource/?p=1745)

This is why we can't have nice things. Get an interview with Netflix VP of communications and waste it by smugly lecturing him.

---

### Post by PC_load_letter on 2010-10-24
I'd say that he was NOT very focused. He should have kept asking one question "if it is working on Roku (which runs Linux), what can be done to make it run on ANY Linux box?". He did ask something like that but it was buried in a crap load of rants about DRM that would turn off someone who is not familiar with the FOSS mentality. 

Maybe the question should actually be directed at Roku, maybe then we'll get a better answer.

---

### Post by BumberBot3K on 2010-10-24
> **PC_load_letter said:**
> I'd say that he was NOT very focused. He should have kept asking one question "if it is working on Roku (which runs Linux), what can be done to make it run on ANY Linux box?". He did ask something like that but it was buried in a crap load of rants about DRM that would turn off someone who is not familiar with the FOSS mentality. 

Maybe the question should actually be directed at Roku, maybe then we'll get a better answer.

I don't think the question needs to be asked at all, because we know the answer: licensing agreements. Media companies won't license their content without DRM. The chosen DRM providers won't build for desktop linux. There is no point in asking cleverly loaded questions in an attempt to trick their PR guy into admitting that he doesn't know much about technology, and then writing snarky articles about how their PR guy doesn't know much about technology.

The only tact that will ever work with Netflix is to say "We are your paying customers, too. We are receiving substandard service compared to other paying customers, and that's not fair. Please use your impressive reputation in streaming media to advocate on our behalf so that we can continue paying you."

---

### Post by clickwir on 2010-10-24
> **MunchySnacks said:**
> Why the heck is this marked as Solved when it is obviously not.....?

While I agree the issue is not solved, it is also not solvable from a Forum. Unless Netflix provides better support, it will continue to be unsolvable. 

The original question of 'can I?' got it's answer. No. It may not be the answer we want to hear, but it is a final answer. Until some company lets Linux users in on the fun, that final answer is best 'solution' we can give someone who asks.

---

### Post by 98cwitr on 2010-10-24
it's what happens when the CEO of Netflix is on the Microsoft Board of Directors

---

### Post by Perkins on 2010-10-26
The problem is that marking a thread as solved when the underlying problem is not causes other people looking for a solution to waste their time reading it, and, when a solution *does* become available, makes said solution much more difficult to find.  There should be a "no solution available" tag or something for marking questions that have no useful answer.

---

### Post by Dubbayoo on 2010-10-27
> **BumberBot3K said:**
> I don't think the question needs to be asked at all, because we know the answer: licensing agreements. Media companies won't license their content without DRM. The chosen DRM providers won't build for desktop linux. There is no point in asking cleverly loaded questions in an attempt to trick their PR guy into admitting that he doesn't know much about technology, and then writing snarky articles about how their PR guy doesn't know much about technology.

The only tact that will ever work with Netflix is to say "We are your paying customers, too. We are receiving substandard service compared to other paying customers, and that's not fair. Please use your impressive reputation in streaming media to advocate on our behalf so that we can continue paying you."

+1. You catch more bees with honey.

---

### Post by robotfire on 2010-11-16
> **Naitsirhc Hsem said:**
> Why should you have to buy a separate piece of hardware to watch something you pay for anyway!!  Netflix should really offer a valid solution or people will keep trying to hack it and get around the DRM.When I made the switch to Linux, I knew about the Netflix issue.  At this point, Netflix wasn't available for my Wii, either.  I'm glad it wasn't, because it forced me to get the ROKU.  I figured that it would be cheaper to buy one box than a million copies of Windows for the rest of my life.  What I *didn't* expect was a box so easy that my 3-year-old figured it out.  It's low power, always on, and it has an awesome interface.  It's beautiful on my 42" flat screen, and who wants to watch a full movie through a computer anyway when you can sit on a comfy couch???

---

### Post by naviathan on 2010-11-19
> **robotfire said:**
> When I made the switch to Linux, I knew about the Netflix issue. At this point, Netflix wasn't available for my Wii, either. I'm glad it wasn't, because it forced me to get the ROKU. I figured that it would be cheaper to buy one box than a million copies of Windows for the rest of my life. What I *didn't* expect was a box so easy that my 3-year-old figured it out. It's low power, always on, and it has an awesome interface. It's beautiful on my 42" flat screen, and who wants to watch a full movie through a computer anyway when you can sit on a comfy couch???
 
I have a HTPC pushing through an HD projector to a 90" screen on my wall.  It currently runs Win7 because of the Netflix issue.  When I first built the box the issue wasn't just Netflix it was also Hulu, which I use a lot.  Now Hulu streams through the Hulu desktop app to Linux, Windows and Mac.  Why can't Netflix do the same?  I would very quickly reformat my HTPC and throw Linux with XBMC on it if I could get my Netflix to run with it.  So to answer your question, I would watch a full movie through a computer, but I would do it from my comfy couch.
 
If someone would build an app and use a closed binary for the DRM I would be happy to pay them $30 US for the app so long as it was well integrated and smooth.  $30 from thousands of people running linux based HTPCs would more than cover the royalty costs for DRM.  Not to mention the number of open source builders who would snatch that program up and integrate it into an off the shelf HTPC solution that goes well beyond the capabilities of a Roku box.  The potential for this support is beyond imaginable.  The fear with this would be on M$ and their constituents.  With a viable DRM solution in Linux they would have no pitch left to save them from losing OEM monopolies.  A Linux to truely compete with Windows and OSX would have to have a generic platform wide (probably kernel integrated) DRM platform for content providers and developers.  I think this would be the show stopper for M$ and they will fight it to the end to keep it from happening.  A generic DRM platform is what is currently keeping Netflix from completing a streaming player for Android.  Don't hold your breath on waiting for that to be released, it probably won't be anytime soon.

---

### Post by beew on 2010-11-19
I am always wondering what is the hype about netflix. What is so special about it that you can't get your content elsewhere? But then again I don't watch TV even, so I don't miss anything. If I want an idiot box I would get a TV instead of a computer.

---

### Post by oldsoundguy on 2010-11-19
> **beew said:**
> I am always wondering what is the hype about netflix. What is so special about it that you can't get your content elsewhere? But then again I don't watch TV even, so I don't miss anything. If I want an idiot box I would get a TV instead of a computer.

The "hype" is the cost.  If you are a cinema buff, 10 bucks a month for the latest releases is a small price to pay.  My brother enjoys that a bunch.  Seeing that he is confined to a wheelchair.  Got him a nice 42" LCD with surround.  Makes his life a bit more pleasurable. (add TIVO and you get the idea.)
Yes, it would be great if Netflix would port to Linux for those that do NOT use Windows .. but do not hold your breath right now.

You can always spend 50-100 bucks and get a net ready Blu-Ray player.. it comes with the Netflix link programmed in (among dozens of others).  All that is needed is to enroll.
All it takes is a home network setup to be able to move content from the Blu-Ray player to your networked computer, if that is what you want rather than an actual stand alone set display.
AND with that set up, you can play ON LINE content from your browser on your TV!

---

### Post by ubot on 2010-12-01
Its annoying really, I wouldn't mind spending a little bit of money on a proprietary application to watch Netflix on Ubuntu.  As far as sitting on the comfy couch, we have our 12 TB Ubuntu media server (Really just 6x 2TB drives on a gamer class motherboard with an i3) parked next to our TV for watching movies, so no Netflix on Ubuntu is annoying.

---

### Post by Slaco on 2010-12-01
> **Perkins said:**
> Yes, it is.  Gstreamer can do it.



Nope.  Plug your device's outputs into your VCR or DVR's inputs and make all the copies you like.  Any Macrovision(tm) protection can be stripped with a filter box available at the local Radio Shack.



Microsoft has made that claim as part of their attempt to lock Linux out of the digital media market.  It is false.  There are a number of programs capable of recording directly off the screen and audio outputs.  Furthermore, even if they somehow managed to disable those, it's still completely vulnerable to hooking your machine up to a recorder device as explained above.  Cables for doing so can usually be found relatively cheaply.


If you can play it, you can pirate it.  Period.


Sure, you can record off the composite output via a VCR, but seriously, who wants to watch what was an HD movie on a 1080p screen from a VCR?

The current Roku boxes do not have have component output, and so using only a Hauppauge PVR is not a solution.

The only real way right now to "pirate" content off a Roku box is via HDMI. The HDMI signal path is HDCP (not Macrovision) protected, and so the only real solution right now is to connect an "HDFury" or another similar stripper & HDMI>Component converter between the Roku and your recorder. An HDFury alone will cost well over $120USD. Money well spent?

---

### Post by seth3d on 2010-12-01
> **ubot said:**
> Its annoying really, I wouldn't mind spending a little bit of money on a proprietary application to watch Netflix on Ubuntu.  As far as sitting on the comfy couch, we have our 12 TB Ubuntu media server (Really just 6x 2TB drives on a gamer class motherboard with an i3) parked next to our TV for watching movies, so no Netflix on Ubuntu is annoying.

I've done sort of the same thing as this and am extremely disappointed NetFlix won't work. 

I'm keeping an eye on Boxee as a viable option. They keep saying that they will have NetFlix integrated "soon". They have already released their Boxee Box which apparently is not only running on a Linux back-end but is running as upgradable firmware rather than hard coded ROM. 

Alternatively, If it makes anyone any happier to read through other peoples disdainful ravings concerning non-working NetFlix, some of them about a piece of equipment they purchased, [look here.]("http://boxee.zendesk.com/entries/86465-the-netflix-app")

I've already integrated the free Boxee software into my Mythbuntu setup using basically the same code as the Hulu integration. I'm ready if there's ever a working update...

---

### Post by Perkins on 2010-12-01
> **Slaco said:**
> Sure, you can record off the composite output via a VCR, but seriously, who wants to watch what was an HD movie on a 1080p screen from a VCR?

The current Roku boxes do not have have component output, and so using only a Hauppauge PVR is not a solution.

The only real way right now to "pirate" content off a Roku box is via HDMI. The HDMI signal path is HDCP (not Macrovision) protected, and so the only real solution right now is to connect an "HDFury" or another similar stripper & HDMI>Component converter between the Roku and your recorder. An HDFury alone will cost well over $120USD. Money well spent?


Well, anyone who doesn't have an HDTV probably won't notice the difference.  If you're picky, you could probably substitute a carefully aligned HD camera.  :P

---

### Post by AKMask on 2010-12-02
dont mind me

---

### Post by rg4w on 2010-12-02
We're facing this issue in our home too:  my gal uses a Mac and prefers NetFlix's selection, but thanks to this thread I've become familiar with the problem on Ubuntu, which I use most of the time.

So for the moment we're going with Hulu.  I've been very pleased that they offer a Linux desktop app - runs great on all my Ubuntu laptops, even my little EeePC 901.

Sure, Hulu's not NetFlix.  But at least Hulu gets it with Linux.  So I'm voting with my pocket book.

We'd like to add NetFlix to the mix, so I've called them to ask about their Linux support (well, I knew the answer but was being polite), and felt obliged to let them know that we have to consider Hulu for now until NetFlix supports Linux.  I was very courteous of course, but equally clear:  no Linux, no money from our house.

If there are indeed enough Linux users to make it worth their while they'll do it.  They just want to make money, like any other company, and if there are enough of us who are earnest about being subscribers and very politely inquire about Linux options for NetFlix sooner or later they'll come around.

---

### Post by seth3d on 2010-12-02
I decided to call their customer support as well,and expressed a desire to have a Linux desktop solution to play NetFlix. The CSR stated they have been getting a lot of calls, and the more calls they get on this the more likely they are to provide a solution. She also stated that they "are working on something" but had no idea what or when. From my experience as a CSR this sort of non-specific information may amount to office rumor but it does give hope.

So! Get on the phone! Be Nice! Be firm in your view!

If you're a subscriber, go to your NetFlix account and click on "contact us" and then "call customer service." This will give you a fast track code to enter which might reduce your wait time. 

I might also add, even if you are a current NetFlix subscriber expressing your opinion without saying "I'm going to leave" still means something. Shipping disks back and forth amounts to a considerable expense for the company. Every person they can get to start using streaming amounts to an overall gain due to fewer disks being shipped. If you can follow my corporate logic, I decide to watch an online video instead of the DVD I have gotten, the shipping cost is displaced into the future. It may not amount to much of a gain for one subscriber, but if you start multiplying it...

---

### Post by tehsilverdollar on 2010-12-08
> **seth3d said:**
> 
I might also add, even if you are a current NetFlix subscriber expressing your opinion without saying "I'm going to leave" still means something. Shipping disks back and forth amounts to a considerable expense for the company. Every person they can get to start using streaming amounts to an overall gain due to fewer disks being shipped. If you can follow my corporate logic, I decide to watch an online video instead of the DVD I have gotten, the shipping cost is displaced into the future. It may not amount to much of a gain for one subscriber, but if you start multiplying it...

I only partially agree.  Bandwidth is not cheap.  At most on the cheap netflix plan you probably go through 6-8 discs a month if you watch the movie as soon as you get it, return it the next day, and it takes a few days to get back to them and have them ship another.  That's still less for them to ship than the cost of your plan even if they're paying full cost for a stamp, but I'm sure they have some discount with the USPS considering the volume they do.

Having worked at many online video content providers I can tell you with certainty that bandwidth costs incurred by heavy users of instant video (especially since it is almost always HD content) are probably incurring more costs for them than those that just use netflix for the delivery service.

---

### Post by snowpine on 2010-12-08
I read an incredible statistic recently that netflix streaming video accounts for up to 20% of total internet traffic during peak viewing hours!

---

### Post by inobe on 2010-12-08
i ended my subscription to netflix and i currently get my dvd's from redbox, and if i wish to see on-demand movies my cable company has pretty much the same movies ready to watch.

i refuse to agree to the windows eul in order to watch stuff at netflix.

---

### Post by Jay Car on 2010-12-08
I don't think there's any good way to resolve the Netflix situation, at least not for me. I cancelled my account and let them know exactly why.  

But I won't beg them to support my OS of choice, and I simply refuse to expend energy and time trying to find a way to make it work on my own.

If a company doesn't want me to access their products and services, so be it. Even if there were an easy work-around I wouldn't use it, it would only reward and encourage their stupid behavior. 

Think about it. Why should any of us have to work twice as hard to see their movies, while paying the same price as those whose systems are supported?  It just makes no sense.  

That doesn't mean I don't watch movies. I just don't use Netflix to watch them.

---

### Post by MountainX on 2010-12-08
> **inobe said:**
> i ended my subscription to netflix and i currently get my dvd's from redbox, and if i wish to see on-demand movies my cable company has pretty much the same movies ready to watch.

i refuse to agree to the windows eul in order to watch stuff at netflix.

Same here. I'm sticking with Linux and Netflix won't get any business from me until they support Linux.

---

### Post by itsjoshjohnson on 2010-12-09
I just think everyone should know it isn't Netflix's fault. Microsoft hasn't released Silverlight for Linux. Netflix uses Silverlight to stream video. They can't stream video if there is no Silverlight for Linux operating systems. So don't take it out on Netflix. Bug MS to release a Silverlight package for Ubuntu.:popcorn:

---

### Post by Perkins on 2010-12-09
> **itsjoshjohnson said:**
> I just think everyone should know it isn't Netflix's fault. Microsoft hasn't released Silverlight for Linux. Netflix uses Silverlight to stream video. They can't stream video if there is no Silverlight for Linux operating systems. So don't take it out on Netflix. Bug MS to release a Silverlight package for Ubuntu.:popcorn:


Roku boxes are Linux based.  So it is possible for them to do it.  Why they won't I have no idea.

There is a version of Silverlight for Linux, it's called Moonlight.  It just doesn't support the DRM that Netflix uses.

There are plenty of non-proprietary methods they could have used to stream their video that wouldn't have left them dependent on the whims of an anti-competitive monopoly.

---

### Post by MountainX on 2010-12-09
> **itsjoshjohnson said:**
> I just think everyone should know it isn't Netflix's fault. Microsoft hasn't released Silverlight for Linux. Netflix uses Silverlight to stream video. They can't stream video if there is no Silverlight for Linux operating systems. So don't take it out on Netflix. Bug MS to release a Silverlight package for Ubuntu.:popcorn:
Netflix chose to use a technology not supported on Linux. The blame lies with that decision.

Many FOSS supporters would not install Silverlight even if it was available for Linux. I wouldn't install it (or Moonlight).

---

### Post by Psyael on 2010-12-10
Netflix is slowly getting there. They avoided (Linux-powered) Android phones for the same reason, but are now on Google TV which is also Android.

Whatever they're doing involving Google TV will trickle down eventually. It will come in a box that is closed source and proprietary, just like StarOffice or Google's apps. I wouldn't get my knickers in a twist about it, but I'm not big on politics. I think an open source operating system is a better model, but never understood why people think every app they run on that system also needs to be wide open.

That said, my monitor is a TV that has Netflix baked into it's firmware, so having my box running while watching movies only sucks up power and makes unnecessary noise. :)

---

### Post by RedRonin on 2010-12-21
I was considering canceling my Netflix subscription.  I think I'll keep it for now, but only because it runs on my Xbox 360.  Like most have mentioned, I'd much rather be able to run it on an Ubuntu based Home Theatre PC instead, so the Xbox 360 can be used for games instead.  I installed Moonlight on my system, and it allows me access to Xbox.com pretty well.  But the new Silverlight based online Gamercards do not display properly for me *(yet)*.  Ah, life...
 :popcorn: 

Red Ronin

---

### Post by inobe on 2010-12-21
gigantic think tank thread is what it is.


btw i canceled my netflix subscription and went with redbox, a big stupid redbox loaded with movies just down the street, two blocks from there is a blockbuster box, push a few buttons and get movies or sit back and watch on demand provided by the cable company, pretty much everything netflix has and then some :lol:

---

### Post by kreppnar on 2010-12-25
Why are they so afraid of LINUX USERS, copyrighting their movies, when a person who uses windows can easy do it as well? Not like it's hard to hook up a DVR to your video out on your computer and record anything that appears through your video card. Ha!..worried about Linux users. Thats not an excuse at all. They make Capture cards, which most dont even work in linux, but all do work in Windows...kind of funny right there.

-Kreppnar-

---

### Post by kreppnar on 2010-12-25
Also, if DRM is keeping people from copyrighting movies in Windows, wouldn't adding it to Moonlight do the same to linux users?? If it is ported correctly, it could operate the same way as it does for Windows. So where is the big deal with that? I think Microshaft, has a deal with Netflix to exclude Linux from this feature. Also another look at the Boxee device. That little thing runs Linux. SO it has a DRM for linux inside of it..and so what kind of crap is that? we could just yank the DRM from that unit, and there yah go.

-Kreppnar-

---

### Post by mellery on 2010-12-27
Does anyone know what part of wine needs work to get silverlight working?  If there were just some bugs in wine that could be fixed to get silverlight working in linux that would be a better option than needed a virtual machine to use watch instantly.

---

### Post by Perkins on 2010-12-27
You can actually install the Windows version of Firefox and Silverlight inside of Wine.  Of course, you have to install an older version of Firefox because Silverlight doesn't work with the latest version.  (Microsoft says that it's Firefox's fault, Firefox says that the only difference in the newer version in any relevant sections of code is what version of Firefox it claims to be...  go figure...)

But the DRM still doesn't work right with Netflix.  (Presently unsure whether it's due to the older version of Firefox or a lack of supporting libraries.)

ReactOS (open source operating system that is binary-compatible with Window$) is progressing by leaps and bounds.  If you have a spare machine you can use to help them with testing, I'm sure they'd appreciate it.  (If you go to test with a virtual machine, turn of any USB support as there currently seems to be a crash-inducing bug with virtual USB for some, inexplicable reason.)  They're getting awfully close to the beta stage, and it would pretty well solve these kinds of issues.

---

### Post by PrvSAT on 2010-12-28
As mentioned in a few posts before. Roku, WDTV Live Plus and all top-set boxes are linux based that offers Netflix. So somehow they got MS permissions and required code to use the DRM.
I believe that it is quite possible if someone knowledgeable would find the time to reverse engineered the firmware of those boxes and further create a plugin or addon for linux users, all linux users would watch netflix. On some top-set boxes the firmware is already hacked but just to bring more features to it.

---

### Post by bitterblackale on 2010-12-29
> **snowpine said:**
> Sorry, you knew it wouldn't work in Linux when you paid for it. ;) Netflix's system requirements are clearly stated in the FAQ; they are not making any deceptive claims or misleading advertising IMHO.

Not true at all. You never know for sure if something will work until you try it. Just because a company said they don't support it, doesn't mean it won't work. Loads of apps which claim they require a Windows pc work in Linux. You just have to try it.

---

### Post by snowpine on 2010-12-29
> **bitterblackale said:**
> Not true at all. You never know for sure if something will work until you try it. Just because a company said they don't support it, doesn't mean it won't work. Loads of apps which claim they require a Windows pc work in Linux. You just have to try it.

I tried it. :)

---

### Post by jimbo99 on 2010-12-29
> **ArtemNY said:**
> 
What the hell is this DRM (digital rights management)? How to fix it?


It's actually called digital "restrictions" management.  Because the big media companies decided it was to negative to say "restrictions" they changed it to say "rights".  That doesn't change the fact that it is a "restrictive" technology that does very little to help legitimate users.

Netflix's main problem is that they decided to go with Silverlight instead of with a known product such as flash.  I think right now that the only real product out there (given there are probably a couple I don't know about) is Silverlight.  Naught else.

There's no reason they can't make DRM work under Linux.  Many media sites have DRM working properly.  So, the only real limit is Microsoft probably not giving the proper support to Linux (in a seemingly uncompetitive way).

---

### Post by joi on 2011-01-15
Use windows for netflix and your problem is solved. There are many things that Ubuntu cannot do and that's is where the beauty of dual booting comes from. Use linux for stuff you wanna use it for and everything else WINDOWS this reduces many problems. whether you like it or not windows does and support more stuff than linux.  I only use linux for fun because i like solving problems inn it :P

---

### Post by Perkins on 2011-01-17
That suggestion is workable for those of us who can afford to blow $160+ on an operating system that we'll rarely use.  Plus the absurd amount of disk space it takes...  But, if you are like I was, as you spend more time "having fun" in linux, you'll start to find yourself cringing whenever you have to go back.  I have one copy of XP on one machine.  I use it for playing the games that don't run under Wine...  A list which seems to be shrinking rather rapidly.  Eventually I doubt I'll need it at all.

---

### Post by light_seeker on 2011-01-21
Works just fine in Ubuntu 10.10 in VM virtualbox running XP.:popcorn:

---

### Post by Chronon on 2011-01-21
> **light_seeker said:**
> Works just fine in Ubuntu 10.10 in VM virtualbox running XP.:popcorn:

Yes, we all know it works fine in XP.

---

### Post by cptrohn on 2011-01-21
I think I saw a toaster that streams netflix the other day! ;)

But seriously it seems like EVERYTHING can stream Netflix these days.... I just use our Wii to stream it, not a huge problem really... Or you can just get a Roku.

I wish they would work on linux support, but probably not happening anytime soon.  I think they have enough business with the Windows/Mac/game console/tv embedded/blu-ray embedded/netflix players etc....


Linux support is just not a priority for them.... besides, there are LOTS of other places on the web to watch whatever you want anyway.

---

### Post by Perkins on 2011-01-22
It might be worth lobbying Blockbuster to add Linux support, since they're the ones playing catch-up and looking for something to give them an edge...  Between the people who would switch for the convenience factor, and the fact that they could probably get at least a little donated coding time if they asked nicely it might be a good move for them...

---

### Post by schanhorst on 2011-01-23
[INDENT]    *Note: Just to clean the table and avoid confusion **before I start**:*
[/INDENT]*1)** I will use the "**L**inux OS" term exclusively for linux distributions targeting desktop/laptop sort of hardware (e.g. debian, slackware, ubuntu, ...) and **_**NOT**_** for linux based OSes **u**sed on mobile devices *[I](like Android OS from Google or iOS from Apple).
[/I]*2) I would like to make clear, that no Netflix but unavailability of DRM functionality on linux OS is the root cause of the issue. And also that DRM is mandatory not because of Netflix but because of policies of whole entertainment industry.*
 ---------------------


I have been reading trough whole this thread quite a while ... 


 Look, the real problem is maintenance ... once you bring a software alive (let say the DRM library for linux OS) it is JUST the first step - the less expensive step when you compare it with expenses going to be thrown in to the maintenance during oncoming years.

Let say somebody implements the first version of DRM for linux OS - let say the Microsoft would do that directly ... Fine, expenses would be let say $100,000 for first working version.
Well, each good manager know, that this expenses are nothing compared to maintain the software trough years (bug fixing, keep the software working on whole variety versions of linux kernels (from old version to most recent), variety of linux OS distributions, variety of hardware platforms where linux can be installed (e.g. imagine just 32bit and 64bit Intel&AMD HW platforms). 

All this maintenance is possible, sure, but it is insanely expensive trough years of life of the software. Imagine - you need to keep whole team of people having detailed know-how about DRM implementation & linux platform (pay them, take car of them ... anybody who was doing something with professional software development will exactly know what I'm talking about ...)

This is not gonna happen without having a revenue from that ... 

~1% of the marked share is assigned to linux OS ([http://www.netmarketshare.com/os-market-share.aspx?qprid=9](http://www.netmarketshare.com/os-market-share.aspx?qprid=9))  
==> BUT take care - this number covers all sorts of possibly existing and active linux OS installations on this earth (all linux OS distributions, big range of kernel versions - even really old, all HW platforms ... in one word 'everything' using linux).
==> So If we remove (from this 1% over all number) such computers which are NOT likely to be interested to use Netflix (e.g. all linux servers, all linux installations outside the US - yes Netflix is available **only** on US territories, all linux installations used for science like physics/mathematics/chemistry ..., and of course all ordinary people using linux on their computers but NOT interested in having Netflix, ...) ==> _then this 1% number will be easily decimated down to something like ~0.1% (and I think this is really VERY optimistic estimation)_

OK, so summing it up, where we got now: On the one side we need to keep expensive team of experienced software engineers to keep DRM library for linux alive AND on the other side potential to target 0.1% of OS marked share ... 

So This is very, very jealous accounting balance - try to present this to any experienced manager and you will be kicked out of the room right after that ...

Almost ALL the people I know they chosen to use linux as they primary OS (as I do for many years already) are also having access to some sort Microsoft OS or Mac OS installed HW (mostly laptop from work). Last x-years you got a laptop in work, so it easily to carry with you from work to home ... ===> Thus, for those people, there is a free option to watch Netflix if they really want. This is shrinking down the 0.1% even more ...

When I started with linux during my college, it was ~1994 it think - I can remember long lasting discussion battles about what is better MS Windows or Linux and why ... these discussion battles were really hot and were able to survive years - even now it is possible to find some of them revamped and still alive here and there ... 
I was fighting for the linux side at that time :)
==> After years of experiences I painfully gained on the field of software development (commercial and scientific field as well) I may say these battles were and are completely pointless, no real-use outcome, nothing useful  ===> and this battle about Netflix on Linux reminds me these pointless battles ...



 Based on Linux OS marked share statistics, its marked share is growing slowly, really slowly (proven by years …) and the speed is not likely to be changed up significantly if at all.  
 For example market share of the iOS (iPhone/iPod/iPad/iSomethongElse) beaten Linux OS about 3 years after introducing it on to the market, and difference is still growing!
Android OS made even bigger mark over linux OS than iOS. 
===> SURE both of them - either iOS from Apple or Android OS from Google are linux based in the background, but that is NOT the real reason why they are successful.  
 The real reason of their success is highly experienced product/project management tightly controlled by BIG commercial companies – it is the common mark for both of them.  
 Do NOT get confused by stack of Free Software+Open Source+Appache Licenses used by Google for Android OS - this open licensing policy does not have anything to do with product success ==> success&quality of resulting product is determined by quality of management and NOT by license (or because it is unix-sort OS)!  
 Apple's management is excellent - top of the top in the hardware/software field in the word - and that you can directly feel on resulting products (and on the price of course). 
*Side note: It is completely different story that Apples licensing polices turned in to one of the most paranoid nightmare in the word. Microsoft was notoriously known in past decades as the one having **most** offensive licensing polices, but what Apple is doing last years on thi**s **field, **it **does not ha**s*[I] a precedence.
[/I]But what is important here - do NOT consider the Android OS or iOS as "linux OS" - as I told, management of this products is based on COMPLETELY different bases, And, by idea they are supposed to serve to different purpose than Linux OS. The main idea of Linux OS is to serve for free with NO hidden commercial side effect, but Android OS and iOS are supposed to make money – indirectly – by creating platform for selling apps, advertisement, entertainment, and all remaining crap ongoing to be just invented how to suck money from customer even more effectively ...


 So summing it up - SilverLight is available (full versions with no restrictions) on Mac OS and iOS (iPhone, iPad). But Android OS is still left behind having the same issue as Linux OS, but not for so long (see [http://blog.netflix.com/2010/11/netflix-on-android.html](http://blog.netflix.com/2010/11/netflix-on-android.html)) – Android is quickly gaining marked share numbers, and it is just the beginning – I believe implementation of DRM functionality will be available on Android soon - I believe it will be distributed exclusively in binary form (no source code freely available).
 If I would see any chance how to get Netflix working natively on Linux OS, this is it – via Android, since I think implementation and consecutive maintenance could be common (with minimal differences) for Android OS and Linux OS.

---

### Post by Don1500 on 2011-01-24
> **light_seeker said:**
> Works just fine in Ubuntu 10.10 in VM virtualbox running XP.:popcorn:

LOC (Load o' Cr*p) Running it in Vbox gives you no proper control of sreen size, all in all a bad experience compared to just booting up in Windows.

In one site this question was raised a poster said that there are any number of open source programmers that would be glad to write the code to make DRM work with Moonlight, for free. If that is so why don't they just do it and get Netflix to work under linux by tricking the server into believing it is looking at a windows machine? I do not mean that a person should be able to do this without a subscription, just work around the Netflix/Microsoft problem.

---

### Post by mellery on 2011-01-24
> **schanhorst said:**
>  If I would see any chance how to get Netflix working natively on Linux OS, this is it – via Android, since I think implementation and consecutive maintenance could be common (with minimal differences) for Android OS and Linux OS.

What do you think about the WINE route?  If wine support for silverlight improved, and the DRM is internal to silverlight then nothing else needs to be added. Other then fixing the issues that keep wine from running silverlight currently.  Those issues aren't DRM related since non-drm silverlight apps currently don't work under wine.

---

### Post by Perkins on 2011-01-24
So far as I know the moonlight developers are working on implementing the DRM support.  However, if what I've heard is accurate, they are basically having to reverse-engineer it since, even though Microsoft points anyone not using Windows at Moonlight, they still won't provide the least bit of help to the project.


The Wine route is a good idea, and it _almost_ works.  Unfortunately, the last time I tried it, I discovered that Silverlight had mysteriously stopped working with Firefox, and Microsoft was claiming it was the Mozilla team's fault, while the Mozilla people were scratching their heads and saying that they hadn't changed anything that should affect it.  The older versions of Firefox it tries, but kind of stutters and dies almost immediately.

I need to find time to build the latest ReactOS and see what it does.  You'd still have to reboot, but at least you wouldn't have to buy a copy of windows.

---

### Post by schanhorst on 2011-01-25
> **mellery said:**
> What do you think about the WINE route?  If wine support for silverlight improved, and the DRM is internal to silverlight then nothing else needs to be added. Other then fixing the issues that keep wine from running silverlight currently.  Those issues aren't DRM related since non-drm silverlight apps currently don't work under wine.

Sure, wine would be a way ... 
I hope wine's guys will try to invent something legal and still working (reverse engineering could  violate license of MS DRM eventually), but I have still feeling that Android OS would be the first guy having DRM working properly. Then it is not so far to port it on desktop type linux OS. This would give native support to linux, no simulation ...

---

### Post by DawgSoldier on 2011-01-31
> **omskates said:**
> You don't even get full access to netflix streaming through the Wii.  You get a "special" list which excludes much of the movies which would be available through a windows os.

This is most certainly not correct. For the first few months we used the netflix disk and it was hard to pick movies so we used the web to select the one we wanted to watch then we picked it up from our que on the Wii.

---

### Post by gtsorbo on 2011-02-19
I haven't tried this out yet, but i think I have a possible solution.

I just set up the Dolphin (Wii) emulator on my Linux box. I learned that you can actually install the Wii menu and other "Channels". I also learned that recently, you could download a channel to do Instant Streaming on the Wii, instead of needing the disc. The Dolphin emulator supports .WAD files for the Wii, so theoretically, if someone got a .WAD file of the Netflix channel, they could use it inside the emulator to stream Netflix content.

Only problem is, I'm not exactly sure how to make the emulator "connected" to the internet. I think there is a way to do it, just not sure how.

---

### Post by ramblinche81 on 2011-02-26
> **princemanjee said:**
> I think you are referring to what is called a USER AGENT SWITCHER or spoofer. Essentially it will tell the web server you are accessing exactly what kind of OS and browser you are using, however the UAS will hijack those requests and fill in anything you choose. I have not seen one for Chrome (haven't looked either). The one for Mozilla works well but not for this purpose. Netflix will still attempt to look for WMP to play the content. If WMP can be ported over to linux - PROBLEM SOLVED. However it is not likely that anyone will do that.
 
Like Netflix HULU uses silver light and if you download moonlight that works fine on HULU for 99.9% of the media (there are exceptions as in olympic coverage and president obama's inauguration to name a few) that had some issues on linux machines because of DRM. Any DRM can be chosen however Netflix has cut a deal with Micro$haft in which M$ provides the DRM encoding software as required by the studios and in doing so M$ locks up its proprietary codec in windows machines along with all of netflix's customers. What I do not understand is if the codec was licensed for use on ROKU boxes and other set top hardware that will play netflix (Wii or other 3rd party players - not just M$ Xbox), why can it not be made available to the netflix clients by SOME means even a binary if an opensource client can not be made?
 
So far the VM is the only way I have gotten it to work and even that kinda sucks (even with 4GB of ram).
 
I wont buy a roku box cause that doesnt solve my problem, I already carry a laptop on the road I dont have room in my bag for an LCD and a roku box. The DVD by mail is useless if I am not home so... Streaming would be nice. However if I can't get it soon Netflix will quickly lose it's utility and be an expense I can do without.
 
I've never been anti MS, but the more I read about how MS controls DRM processes, I am starting to change my mind.
 
MS actions smell like typical anti trust behaviors....the kind of stuff the EUC was very effective at gaining concessions from MS.
 
If MS is blocking DRM resources with some end users and providing restricted license to others, that seems problematic.
 
If MS is telling Netflix they can only provide encoding/decoding utilities to MS OS and exclude others, that seems problematic.
 
I wish some Linux supporting legal minds would review how MS controls DRM for distributors and end users.

---

### Post by gunther222 on 2011-02-28
Well it's one step closer, two steps back.

I changed my user agent string in firefox to..
Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.8) Gecko/20100722 Firefox/3.6.8


and now netflix will let me try to play the videos, but it fails anyway. I'm looking into the differences between moonlight and sliverlight to try and understand why.

However now that netflix thinks I'm coming from a windows box it doesn't just refuse to play out right, it fails handing the video off to moonlight which can't deal with it.


Here's a rather confusing statement from the moonlight pages which make it seem like it supports the PlayReady DRM, which it doesn't.

From moonlights pages.....

** Digital Rights Management **

 Silverlight 2 supports Microsoft *PlayReady* Digital Rights  Management (DRM). This is the DRM solution being used by Netflix's  “Watch Instantly” service for streaming movies to PC (Windows-only) and  Mac computers. 
Status: **unsupported**

---

### Post by joekm on 2011-03-05
Searching around the internet on the DRM issues surrounding moonlight, it appears that Neflix native support on Linux isn't happening soon.  (although Dolphin looks intriguing for a couple reasons - if I can emulate a Wii, I could add that to the guest room).


It may be that the best solution for Linux users is to look at Amazon instant video, Hulu, or maybe iTunes (although I'm not sure if the latter is supported on linux)

I was able to stream a "free" video on Amazon, it appears they use flash so I'm guessing the required DRM is available on Linux.


Amazon is looking pretty inexpensive as well...

---

### Post by CharlesA on 2011-03-05
Another option it to get a bluray player that has streaming functionality. That's what I use.

---

### Post by oldsoundguy on 2011-03-05
> **CharlesA said:**
> Another option it to get a bluray player that has streaming functionality. That's what I use.

Did the same thing and watch on my 55" LCD rather than squeezing it down to watch on a computer monitor. (even though that is a 24" and even bigger than my bedroom set!)

LOTS of streaming audio/video built right into the Blu-Ray players.  Sony has a music channel on demand that has some acts you never see on any other channel.  (they had Dream Theater live in concert on the selections for a while .. not sure if it is still available.)

---

### Post by jimbob on 2011-03-05
I have both a Blu-ray player in the bedroom and the Roku box in the main room.  

Problem with Netflix is they won't stream the newer movies everyone wants to watch, but really old stuff (1940's) and Indie films no one ever heard of.

---

### Post by ladynikon on 2011-03-05
sigh i was hoping this was fixed.

---

### Post by Shibblet on 2011-03-06
I think a lot of people are missing the point.  The point is to be able to play Netflix Streaming videos on your computer.

I have a Netflix enabled Blu-Ray player attached to my TV.  But I'd like to have it work on my netbook, so if I want to watch a different show, I should be able to.  Should, of course, being the operative word.

What happens if I go over to my grandmothers house, who knows exactly nothing about computer, netflix, or even cable TV, and I want to watch a movie on my netbook?

DRM is a p*ss poor excuse by Microsoft, and a bad business decision by Netflix.  They would get more subscriptions if they made their own streaming program for Linux users.  Then it could be included in devices such as XBMC, Linux based Streaming Video devices, laptops, etc.  Not to mention, the up and coming Google Chrome OS Laptop/Netbooks that are soon to be released.

It doesn't even have to be a full fledged application, it can be a browser plugin.

I get tired of excuses, when it seems no one at Netflix is even trying to fix this.

---

### Post by 3177 on 2011-03-07
If MS had control of netflix, Sony and Nintendo wouldn't have rights to it.:P

---

### Post by slooksterpsv on 2011-03-07
Personally, Microsoft should let Netflix strip down a version of windows (XP preferably) to allow Linux users to download XP as a VM to virtualize to watch Netflix.

I run XP in a VM just for Netflix. They could use stupid security policies to lock it down to where only Firefox + Netflix + Silverlight would run. NO IE, NO INTERNET EXPLORER CRAP!

---

### Post by 3177 on 2011-03-07
> **slooksterpsv said:**
> Personally, Microsoft should let Netflix strip down a version of windows (XP preferably) to allow Linux users to download XP as a VM to virtualize to watch Netflix.

I run XP in a VM just for Netflix. They could use stupid security policies to lock it down to where only Firefox + Netflix + Silverlight would run. NO IE, NO INTERNET EXPLORER CRAP!
 no where near the subject,  but....
I use XP in a VBox for diablo. 
That being said, I've run netflix on ubuntu since 9.04.
Need wine though. 1.2.2

---

### Post by Shibblet on 2011-03-07
> **slooksterpsv said:**
> Personally, Microsoft should let Netflix strip down a version of windows (XP preferably) to allow Linux users to download XP as a VM to virtualize to watch Netflix.

I run XP in a VM just for Netflix. They could use stupid security policies to lock it down to where only Firefox + Netflix + Silverlight would run. NO IE, NO INTERNET EXPLORER CRAP!

Look for a program called nLite.

---

### Post by Perkins on 2011-03-07
> **3177 said:**
> no where near the subject,  but....
I use XP in a VBox for diablo. 
That being said, I've run netflix on ubuntu since 9.04.
Need wine though. 1.2.2


Would you care to post a How-to?  For those of us who have been banging our heads against this wall for a long time and haven't managed to find the secret knock by random chance yet?

---

### Post by 3177 on 2011-03-08
okay...
*get the download for netflix player on a windows machine.
*move it to your ubuntu 9.04+ machine with wine.
* install firefox for windows and run in wine.
*install netflix plugin onto WinFirefox(in wine)
never had a problem.
loads okay(could be faster) but I'm not complaining.


you could also run xp in a VB as someone else already said.

---

### Post by mellery on 2011-03-08
Can you explain these two steps please?

*get the download for netflix player on a windows machine.
*move it to your ubuntu 9.04+ machine with wine.

What files need to be copied and where are they located on the windows machine?

---

### Post by E1337ist on 2011-03-08
> **Stray Wolf said:**
> I would think that people willing to pay for viewing content in a digital environment where that isn't necessary shows responsibility on the part of us consumers.  We know we'd be shooting ourselves in the foot by downloading torrents of media for free.  But unfortunately, that's what I end up doing.  If a Linux users money isn't good enough then media barons shouldn't pitch a fit when I have to find creative ways to get the same content other OS users get.
^ this

---

### Post by aysiu on 2011-03-08
> **3177 said:**
> okay...
*get the download for netflix player on a windows machine.
*move it to your ubuntu 9.04+ machine with wine.
* install firefox for windows and run in wine.
*install netflix plugin onto WinFirefox(in wine)
never had a problem. I have. Can you post a screenshot of it actually playing a movie?

I have never gotten it to work in Windows Firefox in Wine in Ubuntu, and I've never seen a convincing case of it either.

---

### Post by slooksterpsv on 2011-03-08
> **3177 said:**
> okay...
*get the download for netflix player on a windows machine.
*move it to your ubuntu 9.04+ machine with wine.
* install firefox for windows and run in wine.
*install netflix plugin onto WinFirefox(in wine)
never had a problem.
loads okay(could be faster) but I'm not complaining.


you could also run xp in a VB as someone else already said.

I want to see a screenshot of this as well. I've tried using Silverlight 3.0 on Firefox in WINE, never got it to work. I should try Boxee it has Netflix support... probably won't work (the Ubuntu version doesn't have Netflix of course). I doubt your suggestion above will work.

---

### Post by Perkins on 2011-03-08
The one thing that's different that I can think of from what I've tried before is that he's downloading the installer program on a Windows machine first, and then installing it under Wine...

I don't suppose you could list the precise version of Wine you're using...  That might make a difference too...

---

### Post by mellery on 2011-03-08
his earlier post mentioned wine 1.2.2

---

### Post by seth3d on 2011-03-09
> **3177 said:**
> okay...
*get the download for netflix player on a windows machine.


Netflix "player" being Silverlight? It won't install for me with wine 1.2.2. I tried this a long time ago. Have you modified your wine configuration or installed any major windows components on wine such as IE6?
This is my output from trying to install silverlight on wine:
```
~/Desktop$ wine Silverlight.exe 

fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:DecryptFileA "c:\\31c1d6821f7518d0a8ac\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"media" (nil) 0x33d980 (nil) 0x33d984 0x33d978 - stub
fixme:advapi:LookupAccountNameW (null) L"media" 0x1428b0 0x33d980 0x148600 0x33d984 0x33d978 - stub
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 3 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 120 ignored L"MsiAssembly" table values

```

---

### Post by Objekt on 2011-03-10
This isn't the ideal solution, and won't satisfy the purists, but I can now watch Netflix streaming through a Windows XP VM.

It would probably also work through a Windows 7 VM, but I haven't tested it.

I was only able to make it work after a recent upgrade to my Nvidia drivers.  

Silverlight performance on a Windows VM seems to be highly dependent on the host system's graphics performance, at least for those of us running an Ubuntu host.  I suspect my solution wouldn't work for those using integrated graphics devices or older drivers.

FWIW.

update:
Almost completely forgot: The Silverlight DRM is pointless anyway.  Anything that I can display on my computer, I can capture on my computer.  A German program called Audials can capture Silverlight streams.

I don't see why anyone would want to, though.  Mostly I just watch TV shows via Netflix streaming.  I've never once gone back and watched a TV show a second time, almost never for a movie.  Life is just too short to watch the same thing over and over.

---

### Post by tshirtdr1 on 2011-03-10
Join the page Add Netflix Support to Linux here:

[http://www.facebook.com/pages/manage/?act=63651803#!/pages/Add-Netflix-Support-to-Linux/131631793574946](http://www.facebook.com/pages/manage/?act=63651803#!/pages/Add-Netflix-Support-to-Linux/131631793574946)

Let Netflix know this is important to us!

---

### Post by Shibblet on 2011-03-11
> **Objekt said:**
> I don't see why anyone would want to, though.  Mostly I just watch TV shows via Netflix streaming.  I've never once gone back and watched a TV show a second time, almost never for a movie.  Life is just too short to watch the same thing over and over.

Agreed.  One of the best things about NetFlix is the ability to watch TV shows that you may have missed.  Commercial free, I might add.

The thing that NetFlix is so worried about is DRM.  Who gives a flying fruitcake!  By the time a movie has made it onto Netflix for streaming, it's been on DVD or Blu-Ray for a couple of months!  If people want to steal it, they've already had the opportunity.

---

### Post by pHr34kY on 2011-03-16
> **Objekt said:**
> I don't see why anyone would want to, though.  Mostly I just watch TV shows via Netflix streaming.  I've never once gone back and watched a TV show a second time, almost never for a movie.  Life is just too short to watch the same thing over and over.

Actually, the movie studios are scared that you'll save the content and share it with a friend, or put it up on TPB right next to the DVD rip that's been there since 3 days before the official release date.

The model is quite broken. Legitimate retailers don't offer movies without DRM, so Linux users have no option but to resort to less-than-reputable sources (i.e. torrents). It's quite clear that the studios don't want our money anyway.

To quote Richard Stallman:
> If you're ever in a situation where you must choose between sharing something with a friend and breaching a license agreement, I recommend you do the lesser of the two evils and breach the license agreement.

Hell, they don't *have* NetFlix in my country. Others exist - my ISP even has one. It won't work on Linux; exact same problem.

---

### Post by Percius on 2011-03-20
1. Wine does not support the base drm that windows has, I suspect it never will. This would be virtually impossible to duplicate these kernel functions even by wines impressive standard.

2. Without the windows DRM methods Sliverlight in wine will never support DRM.

3. Moonlight cannot support windows DRM because dispute microsoft claiming it is a multiplatform platform it is closed source and not released for Linux. The drm specifications are not available.

--> Netflix & Holywood need to get over themselves. They need to realize that the harder they make it to consume legal services the more people will consume illegal services. They need to realize by now there is no Music/Video/Game that cannot be broken. For streaming services you do not need to make it impossible to save the file, just hard. I understand if one creates low lieing fruit virtually everyone will grab it. For such protections flash or a simple drm will do.

For purchased services your own DRM is discouraging people from purchasing it. I should not have to buy a Blueray, buy a dvd for my non blueray TV, and then Buy a android or ipod copy for my android, and still not be able to stream it to my tv via something like boxee.


That said until Netflix and the "Content Owners" realize that they are killing their own industry, I expect you will not see an official version of Netflix on Linux Desktops. The reason is that they cannot lock down linux. The openness of the os prohibits it.

A true DRM on linux is impossible. I would claim its impossible on windows too but more so on linux.

Lets say that someone enabled encryption and created a DRM such that netflix's player could stream encrypted video from the software directly to the driver. 

Someone could simply recompile the kernel and make it so that the dirver connection also output to a file. 

This is the same problem netflix has with Android. When you have full access to the source of the kernel you can change anything they do. 

With the GoogleTV and boxes like roku they are fairly closed. I am sure they can be hacked, but given the users they can be assumed to be a closed.

---

### Post by Perkins on 2011-03-20
The sad thing is that they won't support Linux for fear of people copying their stuff, but all the programs for recording screen and audio output on Windows work just fine.

---

### Post by aysiu on 2011-03-20
Once Amazon gets more than 5000 movies streaming, I may start up Amazon Prime again, since it uses Flash and streams to Linux desktops/laptops and Android phones.

---

### Post by plowdawg on 2011-04-12
I've been looking at the possibilities for Netflix on Linux and I believe that it is highly possible...Netflix uses the Playready DRM from Microsoft and they license a porting kit for it which is $50,000 plus another $25,000 to create.  Looking at the web console on Windows it seems that the player requests parts of the movie every few seconds and this could probably be reversed engineered and ran through the porting kit for the DRM to remove the DRM for a temporary moment while it streams then delete it.  The problem, this is very very pricey and well, though I may like to try on this adventure I just don't know if I would be able to make it in the end and the price is too much for me.

---

### Post by mikefreeman on 2011-05-11
Check this out!

[http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/](http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/)

As soon as this becomes available, problem solved! :D

---

### Post by slooksterpsv on 2011-05-12
> **mikefreeman said:**
> Check this out!

[http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/](http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/)

As soon as this becomes available, problem solved! :D

I'm so excited for that =D

---

### Post by DarkAvneger1337 on 2011-05-14
Cool!

Here's a thought, not sure if it'll work or not, but you COULD download the android SDK, grab an APK of the new netflix app, and test it out. Logic seems sound to me, but I'm not 100% any thoughts?

---

### Post by slooksterpsv on 2011-05-14
> **DarkAvneger1337 said:**
> Cool!

Here's a thought, not sure if it'll work or not, but you COULD download the android SDK, grab an APK of the new netflix app, and test it out. Logic seems sound to me, but I'm not 100% any thoughts?

Yes, Yes, Possibly - you would have to edit a file in order to get it to work, but issue is, that emulating the android OS is slow! Like unbearably slow. When I dev apps for my phone I'm going to just test the apps on my phone.

---

### Post by DarkAvneger1337 on 2011-05-14
worth a try I guess...

[Here's a link to an APK without device check]("http://forum.xda-developers.com/showthread.php?t=1076150")

---

### Post by DarkAvneger1337 on 2011-05-14
It'd be going a bit far, but you could get a virtual machine running with android, and watch from there. It seems like it would solve licensing issues compared to running 'other' OS's to watch netflix.

Or you could just wait...

---

### Post by aysiu on 2011-05-15
> **DarkAvneger1337 said:**
> It'd be going a bit far, but you could get a virtual machine running with android, and watch from there. It seems like it would solve licensing issues compared to running 'other' OS's to watch netflix.

Or you could just wait...
I can't even get it to run on my *real* (rooted) Android phone...

---

### Post by slooksterpsv on 2011-05-15
> **aysiu said:**
> I can't even get it to run on my *real* (rooted) Android phone...

I was able to on my non-rooted phone, LG Optimus S. Colors are messed up like it's trying to render in 3D.

---

### Post by joeoshawa on 2011-05-22
I was reading this out of curiosity due to my computer being an htpc as well. All my entertainment is run through Ubuntu and I have no Interest in changing or using any Microsoft software at all. Now that doesn't mean I hate Microsoft or bill gates in any way. I love Linux and Ubuntu and the whole open source movement and how I can change my operating system in any way I want.  Everyone has the right to choose. I even suggest to people who use and enjoy windows without problems to stay with windows.

Now first off the whole Microsoft should do blah blah blah.  No offence but get real. Do you really believe that Microsoft is going to do anything because of a moral or ethical consideration????  If you do let me start by saying this, Microsoft is a company that makes a thing called software for a device called a computer, Google the rest. Microsoft does not do anything unless it increases the popularity of there OS.

Now one way or the other I am sure companies like Netflix are going to pop up that will support Linux and there is a thousand ways they can deal with the needs of the companies providing the media.  As it stands i would like to use this type of service but if I cannot oh well. I have tons of free and non free media from the Internet as it is and i am more then satisfied with the quality.

As for all the people who keep quoting the problem with multiple distros and window systems as a reason for developers not developing on Linux your just showing that you don't bother to check your info any Linux native program can work on any distro as long as you have the right dependencies unless maybe the developer made that program specifically for one window system on purpose and even then its been made to work.

---

### Post by PVversion666 on 2011-06-18
Hi. I've been lurking on the Ubuntu forums and have finally registered in order to chime in on this subject. 

Unless this is a poorly-timed April Fool's joke, Netflix will be coming to Google Chrome (and Chromium). [Click it, my friend! It's the article that will put a smile on your face.]("http://www.ehomeupgrade.com/2011/05/10/netflix-finally-coming-to-linux-and-chrome-os/")

I can't wait. My wife watches Netflix on her laptop, but alas, we don't have that luxury- at the moment.

---

### Post by MentatGhola on 2011-07-23
Its pretty dumb if you ask me.  Pirates don't need to go to the trouble of catching from a netflix stream.  There are much easier ways like illegal torrents, etc.  Plain and simple.  The reason has to be political.

---

### Post by scu-ba-de-buntu on 2011-08-13
I think the whole process of making it difficult for linux users is a clever ploy to encourage people to stop using mac and windows. You see, I wouldn't mind proprietary OSes if companies didn't go out of their way for anti-features and anti-support of open source OSes. Netflix is encouraging people to make a statistical difference in market-share by installing linux on everything so more and more paying customers are unhappy and stop paying. 

For example, as of the 1st, I'm not a netflix customer anymore. VM are just such a hassle, slow, the wait-time while it fake buffers after a change in Internet speed is slower than HULU's free service commercials, and the resolution is crap.

---

### Post by OpenSorce on 2012-12-20
I know this is an old thread, but searching Netflix Ubuntu still points here so I thought I'd add the following information for new visitors:

[CENTER]**IT WORKS NOW**[/CENTER]

[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

Yes, it uses Wine but the playback and quality are remarkably good.

---

### Post by CharlesA on 2012-12-27
I think this thread has run it's course - last post was back in 2011.

---

