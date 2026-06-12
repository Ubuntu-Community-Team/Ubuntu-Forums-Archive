---
title: "Release Date for Ubuntu Studio?"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by waspinagermanhelmet on 2007-04-04
The Wiki says April... we're now in April... what date in April?<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by fiddler59 on 2007-04-05
As I understand it Ubuntu Studio should be released with Feisty Fawn toward the end of April......
We will see !!!!

David B

---

### Post by frankie0 on 2007-04-12
Think it might be released either the 16th or 19th. Not sure, but I think I read this somewhere. Can't wait!

---

### Post by Aramil on 2007-04-13
Yeah!Cant wait 2!But there is no official announcement about the studio version....I have it in my bookmarks and check every day!lol

---

### Post by MetalMusicAddict on 2007-04-15
It say "April" because thats when it will be out. ;) Its April all month. Comes like that every year.

---

### Post by clapper65 on 2007-04-19
<whine> But I want it now! </whine>

---

### Post by ankara on 2007-04-19
oh, i was really hoping it would be released in line with fiesty today :(

---

### Post by Aurora on 2007-04-19
I just found this:

[www.ubustu.com/globe/2007/04/17/ubuntu-studio-release-date-update/](www.ubustu.com/globe/2007/04/17/ubuntu-studio-release-date-update/)

"We&#8217;re aiming for April"  They've backed off on the April 19th date.

I'm sure our patience will be rewarded.

-Paul in Seattle

---

### Post by jondecker76 on 2007-04-20
I've been checking every day... Also hoping to see the RT kernel patch working with restricted modules...

Do they have anything set up to accept donations?

---

### Post by mrbugspray on 2007-04-20
Hopefully ubuntu studio will be released with ubuntu feisty. They said it would.

Check this page for more info.

[http://digg.com/linux_unix/Ubuntu_Studio_launches_tomorrow_alongside_Ubuntu_7_04_Feisty_Fawn](http://digg.com/linux_unix/Ubuntu_Studio_launches_tomorrow_alongside_Ubuntu_7_04_Feisty_Fawn)

until then, salivate over these screenshots.

[http://www.ubustu.com/globe/wp-content/uploads/2007/04/screenshot666resizedkw1.png](http://www.ubustu.com/globe/wp-content/uploads/2007/04/screenshot666resizedkw1.png)

[http://www.ubustu.com/globe/wp-content/uploads/2007/04/screenshot6xf5.png](http://www.ubustu.com/globe/wp-content/uploads/2007/04/screenshot6xf5.png)

---

### Post by MetalMusicAddict on 2007-04-21
> **jondecker76 said:**
> I've been checking every day... Also hoping to see the RT kernel patch working with restricted modules...
We might release without it and have the kernel in our repos so users can help us test it. Then, we'll re-roll the disks with that kernel. ATM the kernel needs alot of testing that we cant do internally.
> Do they have anything set up to accept donations?
No we don't. We really don't need it. Donate to [Ardour]("http://ardour.org") if you feel compelled. :)

---

### Post by jondecker76 on 2007-04-22
Can I sign up to help with testing?
I have a great setup and can really put the kernel through some tests.

I have a 2.8ghz. 2GB Ram, 720GB HD and an MAudio Delta 1010 and I do a lot of recording work (usually in CuBase or FL)

---

### Post by falkenberg_cph on 2007-04-22
Ubuntu Studio Wiki:
> Due to things beyond our control we will be delaying our release. Hopefully no longer than a couple of weeks. Thank you for your patience.

:cry::cry::cry::cry::cry::cry::cry::cry:


[edit]: i miss having a computer studio - i have gone 100% hardware while waiting.

---

### Post by frankie0 on 2007-04-22
Is Ubuntu Studio gonna be like Feisty with some media applications or is it entirely different? Will  you be able to do everything Feisty can do?

---

### Post by nullfactor on 2007-04-22
Is there a list of hardware that will work with Ubuntu Studio?  I just loaded Fiesty Fawn onto the laptop I hope to run Studio from... my hda-intel hd audio does not work.  If there is a chance that it will work with Studio, then I am a happy camper.  :guitar:

---

### Post by MetalMusicAddict on 2007-04-23
> **nullfactor said:**
> Is there a list of hardware that will work with Ubuntu Studio?  I just loaded Fiesty Fawn onto the laptop I hope to run Studio from... my hda-intel hd audio does not work.  If there is a chance that it will work with Studio, then I am a happy camper.  :guitar:

We have the same HW support Ubuntu-Feisty does.

---

### Post by nullfactor on 2007-04-23
I hear that some people have gotten the hda-intel card to work in Feisty... unfortunately, I've yet to figure that out. :(  I have not given up hope!

---

### Post by deadgobby on 2007-04-23
I thought I read that some programs can be linked up. Right now my Jackd is not running after the upgrade. Yet, it would be sooo freaken cool to link up.
Gobby

---

### Post by MetalMusicAddict on 2007-04-23
> **deadgobby said:**
> I thought I read that some programs can be linked up. Right now my Jackd is not running after the upgrade.

Try this command: **sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'**. Reboot and try again.

---

### Post by deadgobby on 2007-04-24
Thank you very much. But that did not work. Any more help would be great.


1:34:15.278 Startup script...
11:34:15.282 artsshell -q terminate
can't create mcop directory
Creating link /home/doug/.kde/socket-doug-desktop.
11:34:15.638 Startup script terminated with exit status=256.
11:34:15.643 JACK is starting...
11:34:15.647 jackd-realtime -v -R -p128 -dalsa -dhw:0 -r48000 -p1024 -n2
11:34:15.655 Could not start JACK. Sorry.
11:34:17.298 JACK was stopped successfully.

---

### Post by MetalMusicAddict on 2007-04-24
What kernel are you running?

> **deadgobby said:**
> Thank you very much. But that did not work. Any more help would be great.


1:34:15.278 Startup script...
11:34:15.282 artsshell -q terminate
can't create mcop directory
Creating link /home/doug/.kde/socket-doug-desktop.
11:34:15.638 Startup script terminated with exit status=256.
11:34:15.643 JACK is starting...
11:34:15.647 jackd-realtime -v -R -p128 -dalsa -dhw:0 -r48000 -p1024 -n2
11:34:15.655 Could not start JACK. Sorry.
11:34:17.298 JACK was stopped successfully.

---

### Post by deadgobby on 2007-04-24
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=908e0cb9-b793-4cf6-96a9-f3a5cdcb0f4f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic

---

### Post by MetalMusicAddict on 2007-04-24
> **deadgobby said:**
> title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=908e0cb9-b793-4cf6-96a9-f3a5cdcb0f4f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic

Yeah. No wonder. You need the -lowlatency or -realtime kernel. :) The -lowlatency kernel is in the repos.

---

### Post by deadgobby on 2007-04-25
Well I updated the kernal to -lowlatency kernel. I am not to crazy on trying the real time one. I do not feel messing around with a unstable kernal. Still Jackd will not stay on.  I could just wait for studio to come out and deal with it. 

07:01:00.602 JACK was stopped successfully.
07:02:20.420 Startup script...
07:02:20.420 artsshell -q terminate
can't create mcop directory
Creating link /home/doug/.kde/socket-doug-desktop.
07:02:20.755 Startup script terminated with exit status=256.
07:02:20.757 JACK is starting...
07:02:20.757 jackd -v -p128 -dalsa -dhw:0 -r48000 -p1024 -n2
07:02:20.776 JACK was started with PID=9931 (0x26cb).
getting driver descriptor from /usr/local/lib/jack/jack_alsa.so
getting driver descriptor from /usr/local/lib/jack/jack_dummy.so
getting driver descriptor from /usr/local/lib/jack/jack_oss.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
9931 waiting for signals
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
new client: alsa_pcm, id = 1 type 1 @ 0x8059ab8 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
07:02:22.892 Could not connect to JACK server as client. Please check the messages window for more info.
07:02:28.524 JACK is stopping...

---

### Post by JeevesBond on 2007-04-25
I got JACK running on a standard Feisty kernel by typing: 'jackd -d alsa' in a terminal. That was fine for doing some quick editing in Ardour (am still eagerly awaiting the might Ubuntu Studio though of course). :)

That was complete guesswork that led me to doing that, but it did seem to work!

---

### Post by deadgobby on 2007-04-25
that command did the trick. 
jackd -d alsa

---

### Post by sk8dork on 2007-04-27
> **deadgobby said:**
> that command did the trick. 
jackd -d alsa

i enjoy the nice pretty gui app 'jack-control'
it comes up, you click start, it starts jack and has readouts with useful info and a gui where you can configure the links between programs that are using jack. i successfully started jack this way in gnome and fluxbox with the latest feisty, but it wouldn't start in kubuntu. i think it was because of arts or something. this is all on the latest generic kernel.

---

### Post by jondecker76 on 2007-04-27
definitely, jack control is the way to go -  it can take a little tweaking, but it really helps to tune everything in just right

---

### Post by nvrpaul on 2007-04-29
any news about this thing?

---

### Post by mrbugspray on 2007-04-29
Sadly they pushed back the release date. :(

---

### Post by MetalMusicAddict on 2007-04-30
We're actually closing in on the home stretch tonight. We're building test disks tonight and will take the next day or so to test. It will be a couple of days late but it's looking like Friday. :)

---

### Post by jondecker76 on 2007-04-30
thanks for the update!

---

### Post by Aurora on 2007-04-30
> **MetalMusicAddict said:**
> We're actually closing in on the home stretch tonight... It will be a couple of days late but it's looking like Friday. :)

:) :guitar: :) 

  Do you have to do a fresh install, or can you install in an existing Ubuntu?  Because if you can,  I'd like to install Xubuntu on my MacBook using Q (that's the Macified Quemu), then apt-get install ubuntu-studio come Friday or whenever it's ready.  If that's not possible, I'll just wait until it's out and install Ubuntu Studio from scratch.

The MacBook is my music computer, but I tire of Pro Tools and would like to try Wired and Rosegarden on it.  Not too big an Ardour fan, I'm afraid.

Paul in Seattle

---

### Post by sk8dork on 2007-05-01
i think i just crapped my pants.......i am so excited for this weekend.
btw, ubuntu-studio will be a full ubuntu os, utilizing gnome, so you won't be able to install it 'into' xubuntu.

---

### Post by ankara on 2007-05-01
> **sk8dork said:**
> i think i just crapped my pants.......i am so excited for this weekend.
btw, ubuntu-studio will be a full ubuntu os, utilizing gnome, so you won't be able to install it 'into' xubuntu.

im quite excited too, maybe not *that* excited but defo gonna be busy playing this weekend.

what about the update question above, can you do an update/upgrade from edgy/fiesty either from the CD installation disk or from the update-manager? 
suppose its not such a great problem to reinstall. i have a seperate partition for /home.

---

### Post by polaris20 on 2007-05-01
The real test is if I can get the Tascam US-122 working with relative ease.

---

### Post by DJiNN on 2007-05-01
> **sk8dork said:**
> i think i just crapped my pants.......i am so excited for this weekend.

:D

> btw, ubuntu-studio will be a full ubuntu os, utilizing gnome, so you won't be able to install it 'into' xubuntu. 

That's a shame. Xubuntu Music Studio would have been really nice. Gnome is cool & i'll most definitely D/L & give it a go, but i'd love to have it on Xubuntu. 

But whatever, way to go & Kudos to the Ubuntu Studio Team..... Well done guys!
:guitar:

---

### Post by Aurora on 2007-05-01
> **sk8dork said:**
> i think i just crapped my pants.......i am so excited for this weekend.
btw, ubuntu-studio will be a full ubuntu os, utilizing gnome, so you won't be able to install it 'into' xubuntu.

For sure? Because, AFAIK,  I can install the full Ubuntu desktop from Xubuntu, and have a choice of desktop environments when I log on. That's what I read, anyway.  I was hoping to do this with Ubuntu Studio, since I generally prefer XFCE to Gnome.  The main thing is, there is stuff I wanted to do with Ubuntu on the MacBook today or tomorrow.  Could I install the regular Ubuntu to use/tweak for now and install Ubuntu Studio into it later?

And, um, change your pants, OK? ;)

---

### Post by polaris20 on 2007-05-01
Seeing as how Ubuntu Studio is using the regular repositories, I don't see why you can't just install UbSt, then go to the repositories and add XFCE, and then change your default WM.

---

### Post by sk8dork on 2007-05-01
> **polaris20 said:**
> Seeing as how Ubuntu Studio is using the regular repositories, I don't see why you can't just install UbSt, then go to the repositories and add XFCE, and then change your default WM.

that's true. this might work. i am not sure whether or not you could install it from inside a previous installation like xubuntu, though, and have it work the same (say, the way that you can install kubuntu from inside ubuntu, etc.). not sure if it would be the best idea.

---

### Post by mrbugspray on 2007-05-01
I hope Ubuntu studio comes out soon... Then I can stop pacing all day, every day in my office waiting for it to be released...

---

### Post by JerseyShoreComputer on 2007-05-01
One of my tech guys told me today that it is due to be released on Friday. I've tried to do some searching and I can't verify that, but let's keep our fingers crossed. I'd really like to get it installed!!

---

### Post by sk8dork on 2007-05-01
> **JerseyShoreComputer said:**
> One of my tech guys told me today that it is due to be released on Friday. I've tried to do some searching and I can't verify that, but let's keep our fingers crossed. I'd really like to get it installed!!

let me see if i can get that verified for you. one sec...

> **MetalMusicAddict, on the UbuntuStudio dev team said:**
> We're actually closing in on the home stretch tonight. We're building test disks tonight and will take the next day or so to test. It will be a couple of days late but it's looking like Friday. :)

ther ya go =) (top of page 4 in this thread)

---

### Post by sclough on 2007-05-01
In line with the guy asking the question about installing studio from an xubuntu install..  I feel like this is a stupid question, but my understanding is that studio is only being released on dvd because of the size of the packages and the machine I want to put it on does not have a dvd player.  I was assuming I could just use the alternatives cd and do a minimal (i.e. server type) ubuntu install and then just apt-get ubuntu-studio.  That way I won't have any cruft laying around from ubuntu/kubuntu/xubuntu to deal with.  I'm assuming the studio guys have tweaked things enough that it's best not to overlay studio on x/k/ubuntu like you normally can with installing kde or xfce along side the standard ubuntu to get alternative window managers.  Is there any reason my approach wouldn't work or a better way?

Anxiously awaiting Friday...:D

---

### Post by polaris20 on 2007-05-02
> **sclough said:**
> In line with the guy asking the question about installing studio from an xubuntu install..  I feel like this is a stupid question, but my understanding is that studio is only being released on dvd because of the size of the packages and the machine I want to put it on does not have a dvd player.  I was assuming I could just use the alternatives cd and do a minimal (i.e. server type) ubuntu install and then just apt-get ubuntu-studio.  That way I won't have any cruft laying around from ubuntu/kubuntu/xubuntu to deal with.  I'm assuming the studio guys have tweaked things enough that it's best not to overlay studio on x/k/ubuntu like you normally can with installing kde or xfce along side the standard ubuntu to get alternative window managers.  Is there any reason my approach wouldn't work or a better way?

Anxiously awaiting Friday...:D

Maybe your answer is somewhere in here. 

[http://oktyabr.wordpress.com/2007/01/27/ubuntu-studio-an-interview-with-project-manager-cory-kontros/](http://oktyabr.wordpress.com/2007/01/27/ubuntu-studio-an-interview-with-project-manager-cory-kontros/)

---

### Post by sclough on 2007-05-02
He mentions the different apps in studio, but not installing the whole studio the way I was thinking.  I'm pretty sure what I'm thinking will work based on the comments from the Ubuntu week IRC last week with one of the other studio leads.

---

### Post by Aurora on 2007-05-02
> **polaris20 said:**
> Maybe your answer is somewhere in here. 

[http://oktyabr.wordpress.com/2007/01/27/ubuntu-studio-an-interview-with-project-manager-cory-kontros/](http://oktyabr.wordpress.com/2007/01/27/ubuntu-studio-an-interview-with-project-manager-cory-kontros/)

You're right.  Metal Music Addict said::

"Also a goal of the project was that anyone could use the metas so if you run Kubuntu you could &#8220;sudo apt-get install ubuntustudio-audio&#8221; and it will pull everything for you&#8230;  So if you don&#8217;t want a new install you can simply grab a suite."

Sweet.  I'll get working on the MacinBuntu tonight.

PD

---

### Post by sclough on 2007-05-02
> **Aurora said:**
> You're right.  Metal Music Addict said::

"Also a goal of the project was that anyone could use the metas so if you run Kubuntu you could “sudo apt-get install ubuntustudio-audio” and it will pull everything for you…  So if you don’t want a new install you can simply grab a suite."

Sweet.  I'll get working on the MacinBuntu tonight.

PD

I took that more as you could install one of the suite of applications (audio/video/graphics) vs. the "Ubuntu Studio" distro, but maybe I misinterpreted.

---

### Post by sk8dork on 2007-05-02
> **sclough said:**
> I took that more as you could install one of the suite of applications (audio/video/graphics) vs. the "Ubuntu Studio" distro, but maybe I misinterpreted.

yeah, i already installed all of the meta packages in the feisty repos onto my ubuntu machine at home. those mata packages do not an ubuntustudio make. i'd imagine you would miss out on the kernel they're going to ship with it as well as all of the configurations and theme. but that stuff would probably be combined into an ubuntustudio-desktop package, as we've been discussing.

---

### Post by MetalMusicAddict on 2007-05-02
> **sk8dork said:**
> yeah, i already installed all of the meta packages in the feisty repos onto my ubuntu machine at home. those mata packages do not an ubuntustudio make. i'd imagine you would miss out on the kernel they're going to ship with it as well as all of the configurations and theme. but that stuff would probably be combined into an ubuntustudio-desktop package, as we've been discussing.

At launch we're not shipping a kernel that you cant get right from Ubuntu. We'll ship -lowlatency at 1st. We will however be testing a -realtime kernel with help from you guys. ;)

We also have our own small repo with some updated packages.

---

### Post by Aurora on 2007-05-02
Well, in light of all this, I think I'd rather wait 2 or 3 days for Ubuntu Studio to come out, and just add the few extra packages I need for non-multimedia stuff. That should create a lighter install, without OpenOffice, GAIM, Ekiga, and other things I don't really need.  The thing is, I've been waiting to use the "few extra" things for weeks. and am keeping others waiting for the output of those apps, so it makes it seem like a long 3 days!

---

### Post by Shay Stephens on 2007-05-02
Can't wait!  Really looking forward to this!

---

### Post by lyall on 2007-05-02
Hi All
I am using Feisty Fawn (Kubuntu) and I found UbuntuStudio in Synaptic Package Manager
the packages are as follows
ubuntustudio-audio
ubuntistudio-graphcis
ubuntustudiolauncher
ubuntustudio-video 

Been using it for over a week now, it did install a lot about 250MB 
There are a lot of options to use


Good Luck and have Fun :) 
:guitar:

---

### Post by mrbugspray on 2007-05-02
Man... I've been pacing all day everyday, stopping every couple of hours for food and water, checking every five minutes to see if it's released. Hopefully the ubuntu studio team will keep their promise about it to be released on Friday.  can't wait for it ubuntu studio to come out. ](*,)
see:

[http://www.ubustu.com/globe/2007/04/30/holy-hot-damn-release-date-info/](http://www.ubustu.com/globe/2007/04/30/holy-hot-damn-release-date-info/)

---

### Post by Aurora on 2007-05-02
> **mrbugspray said:**
> Man... I've been pacing all day everyday, stopping every couple of hours for food and water, checking every five minutes to see if it's released. Hopefully the ubuntu studio team will keep their promise about it to be released on Friday...]

Whew, deep, slow breath time.

I'm telling myself that Friday is a goal rather than a promise, that way I won't be so anxious about the exact time.   I hope.  OK, a little anxious.

PD

---

### Post by delmore on 2007-05-02
Those packages are NOT Ubuntu Studio. They are very old.

NOT NOT NOT NOT NOT NOT NOT Ubuntu Studio ;)

SOON!!!!!!

---

### Post by sk8dork on 2007-05-03
the ubuntustudio wiki has been updated a little. there's some new eye candy in the artwork section =D

---

### Post by Endolith on 2007-05-03
*paces back and forth*

I actually am trying not to get my hopes up too high:  DeMuDi didn't work as well as I wanted, PlanetCCRMA didn't work as well as I wanted, etc.

This is a first release so I shouldn't have toooo high expectations.  On the other hand, I'm very happy with Ubuntu itself, so maybe this has a chance to work!  I hope so.

---

### Post by mrbugspray on 2007-05-03
THEY JUST RELEASED THE RELEASE NOTES!!!!!!!!!! (Problem is, I can't find a download...) 
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

[https://wiki.ubuntu.com/UbuntuStudio/Feisty/ReleaseNotes](https://wiki.ubuntu.com/UbuntuStudio/Feisty/ReleaseNotes)

Hopefully I will of the ubustu download link soon...

---

### Post by IanW on 2007-05-04
That's an empty wiki page.

---

### Post by jagwah on 2007-05-04
It wasn't empty earlier on in the day, it actually had the release notes there. Speaking in the 'past' tense, as if it was after the event (release).

---

### Post by Endolith on 2007-05-04
> **IanW said:**
> That's an empty wiki page.

It wasn't empty yesterday :-)

---

### Post by ankara on 2007-05-04
i could explode with anticipation :)

---

### Post by sk8dork on 2007-05-04
> **ankara said:**
> i could explode with anticipation :)

i'm kinda disappointed in the choice of Pitivi as the video editor. i know that we can easily install other more capable editors like lives (i found out yesterday that a deb exists at getdeb, no more compiling from source), cinelerra, kdenlive, etc. i am sure this decision was made for a very good reason, like cinelerra licensing issues and unavailability of other apps. hopefully the inclusion of pitivi will get it more exposure, advance the development, and all that good stuff. i played with it last night for the second or third time ever, and good lord it is basic and buggy. perhaps ubustu will will bring out a newer version. that would be great. if not, i'll just have to install the other video editing apps in the meanwhile, which isn't terrible.

so to summarize, i'm a little disappointed in the circumstances, not at all disappointed in the ubuntustudio team.

---

### Post by tbfr on 2007-05-04
> **Endolith said:**
> It wasn't empty yesterday :-)

True: [https://wiki.ubuntu.com/UbuntuStudio/Feisty/ReleaseNotes?action=diff]("https://wiki.ubuntu.com/UbuntuStudio/Feisty/ReleaseNotes?action=diff")

---

### Post by fiddler59 on 2007-05-04
I'll be amazed if it is released by the end of the day.........I think the developers are more conserned with getting things right, so it could be a few days late  (I hope not !) ........

David B

---

### Post by Endolith on 2007-05-04
> **fiddler59 said:**
> I think the developers are more conserned with getting things right, so it could be a few days late  (I hope not !) ........

It's already a few days late!  :-)

> Coming this April...

---

### Post by DJ Wings on 2007-05-04
[It's on Digg.](http://digg.com/linux_unix/RELEASED_Ubuntu_STUDIO#c6520884) Of course, it's not really out yet... I would have spooged my pants by now if it was.
EDIT: Oh, wait... Too late for that. Behold, [a report on Feisty's laptop-hardware compatibility](http://digg.com/linux_unix/Ubuntu_7_04_Feisty_Fawn_on_Toshiba_Fingerprint_reader_Wireless_Core_2).

---

### Post by super.rad on 2007-05-05
On the IRC chat room topic it says this "Release Date: Joe Jaxx says "What Do We Have Here??"
[http://xs315.xs.to/xs315/07182/screen0.png]("http://xs315.xs.to/xs315/07182/screen0.png") AND [http://xs315.xs.to/xs315/07182/screen17.png]("http://xs315.xs.to/xs315/07182/screen17.png")

---

### Post by P_Badger on 2007-05-05
> **sk8dork said:**
> i'm kinda disappointed in the choice of Pitivi as the video editor.


I agree. Pitivi is almost useless. Hopefully the future will bring a better video editor to Ubustu. 

Audio editing apps are *incredible* on Linux, I may even be able to bring a couple of friends over to Linux once I show them Hydrogen, Ardour 2, and Jamin. But (full-featured and working) nle's are lacking.

---

### Post by DJ Wings on 2007-05-05
Audacity ftw. I've made some basic remixes using nothing more than Audacity and the multitrack files to some NIN songs (publicly and freely available online). Hydrogen is also pretty good, but Ardour is a PITA. There's some bug where if I'm not playing something, I get a crapload of feedback in my headphones.. Very annoying. Maybe it's just JACK.

---

### Post by MetalMusicAddict on 2007-05-05
> **P_Badger said:**
> I agree. Pitivi is almost useless. Hopefully the future will bring a better video editor to Ubustu.

The PiTiVi choice was made because it has a better base than the others because it uses gstreamer. This is good because codec support support isnt hard-coded in. Cinelerra, while a killer application just has too many issues to get into free distros atm. PiTiVi will come along. It has active development and is backed by Fluendo.

---

### Post by Endolith on 2007-05-05
> **DJ Wings said:**
> Audacity ftw. I've made some basic remixes using nothing more than Audacity and the multitrack files to some NIN songs (publicly and freely available online). Hydrogen is also pretty good, but Ardour is a PITA. There's some bug where if I'm not playing something, I get a crapload of feedback in my headphones.. Very annoying. Maybe it's just JACK.

That's probably just JACK.  I ran into some weeeeird Ardour bugs back in the day when I tried it, like rewinding while writing a volume envelope would write a second backwards envelope at the same time as the forwards one!  It made no sense.  And weird crashes and such.  I have a feeling all those kinds of bugs are worked out by now, though.  I really really want Ardour to work well and to be my new best friend.

---

### Post by DJ Wings on 2007-05-05
I personally find Ardour a major pain to use. Hydrogen and Audacity, I was able to use pretty much right away, but Ardour breaks pretty much all the rules of UI standardization. It uses GTK? Riiight...

---

### Post by ankara on 2007-05-06
ardour is awesome, you just need to be patient and willing to learn.
you cant expect to have the software write the music for you.

---

### Post by adamadamant on 2007-05-06
True thing this man said. Ardour is awesome. I was a bit put off at first and used to use Rosegarden for audio, but if you sit down for a few minutes it's not that hard to get the hang of and it's way superior for recording loads of tracks. Also, unless it's my imagination, Audacity won't use Jack, which is really silly and makes it unusable for me.

---

### Post by neptoon on 2007-05-06
> **DJ Wings said:**
> I personally find Ardour a major pain to use. Hydrogen and Audacity, I was able to use pretty much right away, but Ardour breaks pretty much all the rules of UI standardization. It uses GTK? Riiight...
The new version 2.0 of Ardour has seen a lot of improvements in the GUI (at least that's my impression). I'm using it since some days.

---

### Post by P_Badger on 2007-05-06
Ardour 2.0 is pure love. It truly is the closest one is going to get to Protools in Linux, and yes, I've used Protools. 

And much like Protools, Ardour isn't going to make your music for you, you have to learn to use it.

---

### Post by ankara on 2007-05-06
audacity can be compiled with jack support but for some strange reason the ubuntu repositories have audacity compiled without???? :confused: 

its not too hard to compile your own version, but i would have hoped that for the Ubuntustudio, they might have updated the package.

---

### Post by MetalMusicAddict on 2007-05-06
> **ankara said:**
> audacity can be compiled with jack support but for some strange reason the ubuntu repositories have audacity compiled without???? :confused: 

its not too hard to compile your own version, but i would have hoped that for the Ubuntustudio, they might have updated the package.

We use packages right from the Ubuntu repos. There's no difference. That being said there seems to be a issue with Audacity's JACK support. Thats why its not there.

---

### Post by BobboProfondo on 2007-05-07
It looks as though a date was edited [here]("http://www.ubustu.com/globe/2007/04/30/holy-hot-damn-release-date-info/") but I haven't seen anyone else mention that Ubuntu Studio might be released today...

Anyone know any different?:confused: 

Cheers:

---

### Post by ankara on 2007-05-07
ah dont worry about the bloggers, they need to build hype to survive ;)
keep your eye on the main page and here imo. MMAdict is here and thats good enough for me.

ive held off updating to fiesty as im waiting for Ubstudio, from whats been said it sounds like ardour2 is packaged in the fiesty repos; is this so? it would save me another 2 hour compile and make me very happy ..

---

### Post by neptoon on 2007-05-07
> **ankara said:**
> 
ive held off updating to fiesty as im waiting for Ubstudio, from whats been said it sounds like ardour2 is packaged in the fiesty repos; is this so? it would save me another 2 hour compile and make me very happy ..

AFAIK ardour2 is one of the few packages that will be in a special ubuntustudio repository instead of the official ubuntu repos.

---

### Post by P_Badger on 2007-05-07
> **ankara said:**
> ah dont worry about the bloggers, they need to build hype to survive ;)
keep your eye on the main page and here imo. MMAdict is here and thats good enough for me.

ive held off updating to fiesty as im waiting for Ubstudio, from whats been said it sounds like ardour2 is packaged in the fiesty repos; is this so? it would save me another 2 hour compile and make me very happy ..

Or you can just go get an Ardour 2 deb from here..

[http://www.getdeb.net/release.php?id=811](http://www.getdeb.net/release.php?id=811)

---

### Post by DJ Wings on 2007-05-07
I'm going to have an Ubustu vs. dyne:bolic shootout on my blog. And so far, it doesn't look good for Ubustu (I have a category for punctuality)...

---

### Post by dmg025 on 2007-05-07
**Bump**

---

### Post by MetalMusicAddict on 2007-05-07
> **DJ Wings said:**
> I'm going to have an Ubustu vs. dyne:bolic shootout on my blog. And so far, it doesn't look good for Ubustu (I have a category for punctuality)...

lol. Etch sux because it was late.

---

### Post by sk8dork on 2007-05-07
> **MetalMusicAddict said:**
> lol. Etch sux because it was late.

and dyne:bolic has been released for a while, and was already in development for a long time. can't really compare releases on a time basis here.

---

### Post by Shay Stephens on 2007-05-07
> **sk8dork said:**
> and dyne:bolic has been released for a while, and was already in development for a long time. can't really compare releases on a time basis here.

If you are completely irrational, anything is possible!

---

### Post by DJ Wings on 2007-05-08
In any event, any updated estimates on when it'll be out?

---

### Post by Endolith on 2007-05-08
> **DJ Wings said:**
> In any event, any updated estimates on when it'll be out?

It's going to be released sometime in April. :)

---

### Post by sk8dork on 2007-05-08
> **Endolith said:**
> It's going to be released sometime in April. :)

actually, according to [http://ubuntustudio.org/](http://ubuntustudio.org/) it's 'coming soon'. and according to the wiki, it's May 2007. i'm so glad they finally changed that =)

---

### Post by BobboProfondo on 2007-05-08
> **sk8dork said:**
> actually, according to [http://ubuntustudio.org/](http://ubuntustudio.org/) it's 'coming soon'. and according to the wiki, it's May 2007. i'm so glad they finally changed that =)

Woo hoo! Coming soon. I've been sat here at my desk awake since 19th April. Soon I can sleep...:shock:

---

### Post by samba on 2007-05-08
i can't wait!!! i'm really looking forward to trying it...

:guitar: 

vince

---

### Post by MrGadget on 2007-05-08
> **samba said:**
> i can't wait!!! i'm really looking forward to trying it...

:guitar: 

vince

muahahahaha me tooo :-\"

---

### Post by MetalMusicAddict on 2007-05-08
> **sk8dork said:**
> can't really compare releases on a time basis here.

Exactly my point. ;)

---

### Post by mrbugspray on 2007-05-10
UBUSTU IS OUT!!!!!!!!!!!!! NO MORE PACING AND OBSESSING!!! DOWNLOAD IT!!!

ubuntustudio.org

---

### Post by Endolith on 2007-05-10
> **mrbugspray said:**
> UBUSTU IS OUT!!!!!!!!!!!!! NO MORE PACING AND OBSESSING!!! DOWNLOAD IT!!!

ubuntustudio.org

ZOMGZ!!!!!!!!!!!!!!!!!!

---

### Post by Endolith on 2007-05-10
So, to do this without a DVD burner, we install a minimal Feisty and then follow the directions on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) ?

---

### Post by mrbugspray on 2007-05-10
Just finished the "conversion!" It's THE BEST! :-D :-D :-D :-D :-D :-D :-D :-D

---

### Post by mrbugspray on 2007-05-10
> **Endolith said:**
> So, to do this without a DVD burner, we install a minimal Feisty and then follow the directions on [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) ?

That's exactly what I did.

---

### Post by Endolith on 2007-05-10
> **mrbugspray said:**
> That's exactly what I did.

Ok.  I should have downloaded the Feisty CD before tonight!  Still at 32%.  :-)

---

### Post by samba on 2007-05-10
Great great great! i'm erasing my hard drive and installing it now! :-):-) yahoo!!!

---

### Post by DJ Wings on 2007-05-11
About time. I noticed the sizeable package list... But seriously, this probably could have been put on a CD.

---

### Post by sk8dork on 2007-05-11
hmm...wonder what's wrong...joejaxx disabled everything on the ubuntustudio.org site.

---

### Post by stuffradio on 2007-05-11
So... is there a link to the downloads elsewhere than?

---

### Post by IanW on 2007-05-11
Maybe we've crashed the server by all jumping in at once?

The torrent is showing up at several BitTorrent trackers, as well as Distrowatch.

---

### Post by Shay Stephens on 2007-05-11
> **IanW said:**
> Maybe we've crashed the server by all jumping in at once?

The torrent is showing up at several BitTorrent trackers, as well as Distrowatch.

I am downloading the torrent now and getting good speeds.  Had to use ktorrent though.  Bittorrent is way too slow on my computer.

---

### Post by Aurora on 2007-05-11
I wish I understood more about torrents.   I'm getting KB/s speeds in the 30's...looks like a 6-8 hour download, just like Feisty was.  I *could* just wait a day, when it will take about 20-30 minutes, but I'd rather have it in 8 hours than tomorrow.

I'm handicapped by the fact that I want to dowload to my HFS+ formatted Firewire drive, which Linux can read, but not write to, so I'm using my MacBook.  Then I can burn UStu DVDs wherever I am.

If you can come up with a better nickname than UStu <yuck>, please do. Ubuntu Studio is too long to type.

---

### Post by Shay Stephens on 2007-05-11
I am now running Ubuntu Studio!  It looks great, and I am getting it all setup now.  I hope to get to work on it tonight.  Have some video to render and burn, so this will be a good test.

---

### Post by ffxr on 2007-05-11
can we keep the first thoughts coming fella's please..?

im installing it tomorrow.. and its a bit of mare finding ways to feed my excitement with information, with the main website down.

---

### Post by ankara on 2007-05-13
just one or two annoyances so far, the theme makes for difficult reading when in the lighter grey colour when viewing at 1600x1200 and grub keeps giving me a very annoying error 17:
ive been looking throught forums and have found that using the instalation cd going to "boot from first hard dik" then choosing ubstudio works fine.

oh for an easy way to choose lilo.....

---

### Post by ankara on 2007-05-13
ok sorted the grub issue. /grumbles

latency is pretty much inaudible, reduced to a very slight phase, when playing both direct and through jack applications. 

:)

---

### Post by Endolith on 2007-05-13
> **ankara said:**
> just one or two annoyances so far, the theme makes for difficult reading when in the lighter grey colour when viewing at 1600x1200

Agreed.  It's pretty for screenshots, but without *everything* being converted to the same style (including the terminal, web pages, etc.) it is difficult to read.   Especially light grey text on a white background.

Also, it's not possible to open FLAC files in Ardour?

---

### Post by sk8dork on 2007-05-19
i installed ubuntu studio. i like it a lot. i don't like gnome so much because it just feels sluggish. i installed fluxbox. i missed the gnome ubuntu studio theme. i use gnome-settings-daemon to maintain the innards theme, and i modified the images from the gnome theme to work in a fluxbox theme. this is the result. beautiful. go ahead and compare it to the gnome theme, it is very close. this is a first revision. look at it very closely and let me know what you think.

[_link_ to the screenshot](http://www.flickr.com/photo_zoom.gne?id=504101914&size=l) [[here's a _full rez shot_ if you need it-1600x1200]](http://www.sk8dork.com/pics/ubustu-fluxboxtheme1.png)

this is the first fluxbox theme i've ever created.

i think you can see all there is to see in the theme with what i have up. the menu breaks out, got unfocused windows and focus windows, and have one button pressed emitting the blue glow. if anyone wants the theme for themselves i might make it available, if it's ok with the ubuntu studio team.

i'd like to know what everyone thinks. [URL="http://www.sk8dork.com/2007/05/ubuntu_studio_with_fluxbox_the.html"]_spread the word!_
[/URL]

edit: already fixed up some things [_[full shot]_]("http://www.sk8dork.com/pics/ubustu-fluxboxtheme2.png"). much better.

edit: and better still. [link]("http://www.sk8dork.com/pics/ubustu-fluxboxtheme3.png")

edit: the last one actually was kinda messed up in certain ways. i present to you, ubustu-fluxboxtheme rev4. [link](http://www.sk8dork.com/pics/ubustu-fluxboxtheme4.png)
i think i am close to being done, if not already there.

---

