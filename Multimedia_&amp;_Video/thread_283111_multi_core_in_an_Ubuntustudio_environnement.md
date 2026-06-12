---
title: "multi core in an Ubuntustudio environnement"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by damu on 2006-10-23
Hi,

I am using STG for music production and play with Ubuntu from time to time for sound design. In both cases, I noticed that a linux based system for audio production is not optimised for more than one core. 
I think  it's a very serious subject  for Ubuntustudio :

- Every forum about 'sound production on a PC' would suggest to go for dual core when building a DAW. Before dual core, the state of the art platform was dual opteron. 

- Jack is not optimized for multicore. Therefore, we have the result of Mac or Windows few years ago : one core used for the heavy processing - audio- and the second core used only for graphic the system. I jus't don't want to think what it gives with quad core (coming very soon with Intel and 2 dual core processors with AMD). 

- [Jackdmp]("http://www.grame.fr/~letz/jackdmp.html") seems to be an answer to this issue. I managed to install it and run it on Ubuntu (I didn't try on STG, as I need an up and running environnement for audio prod and that's what STG is for me). I tried it on Ubuntu edgy with the stock kernel. 

To test it, I used zynadd with 7-8 layers of sound (on the same midi channel) through Jackrack with mostly Gverb (probably the most power hungry effect). The results were better than with Jackd. It seems though that was still some room for improvment. It might be a question of tweaking it properlly.
It's probably worth mentionning that I had a problem starting Jack last time...
If we could go further in this investigation, see what works and not with jackdmp, how it can be optimized, see if a deb could be packaged , etc, it might help delivering a better experience for musicians on Ubuntu :)

---

### Post by techrush on 2006-10-23
First i dont think this is an ubuntu studio issue at all. Although it has everything to do with linux as an audio platform. I think maybe our/your efforts would be better spent trying to provoke the linux audio developer community as a whole to look into multi threading. 

This is probably a ton of work to convert an app which didnt fully utilize dual cores into a fully multithreaded beast. If i had to geuss id say this will take quite some time to catch on in the linux audio world. Which is really a damn shame considering a lot of the major windows/OS X apps are already smp capable/multithreaded. 

There is a linux audio developer mailing list that you could probably get some more info about this from.....just a FYI

---

### Post by damu on 2006-10-29
My point isn't that "Ubuntu Studio"  should take in charge the developpement of multithreaded versions of audio apps...that could take years...;) 

But packaging the best of what is available in the linux world, in the "ubuntu spirit" - ie easy to use/implement for a non techi (through GUI and not command line) doesn't seem to be out of context.

Some "linux apps" are already multithreaded .Ardour comes to mind :

["Ardour is extensively multi-threaded so it will use the processors for a combination of GUI, audio processing, and disk I/O. However, the realtime audio processing thread will only ever use one processor, so you won’t see a benefit in plugin count with multiple CPUs. That said, the interface will be much more responsive on multi-processor/core systems with large plugin-heavy sessions."]("http://ardour.org/node/433")

The core application to be optimized for real time processing is Jack.
Jackdmp is an answer to this issue. It exists, can be downloaded and tested. Here are the comments of one jackdmp user :
[URL="http://www.nabble.com/Jackdmp-0.57-package-for-Linux,-OSX-and-Windows-t2177429.html"]
"> I must say I'm pretty amazed at the performance, if I'm not  
> mistaken I'm seeing a nearly 50% reduction in cpu usage on some of  
> my larger projects... impressive indeed.
> Thanks again for the fix and the excellent work. "[/URL]

Sooo, I went on testing a bit:

For a while , I had a problem starting jack with jackdmp option. It couldn't find the file libjackdmp.so [I tried to follow part of this]("http://www.medienwissenschaft.hu-berlin.de/mwiki/index.php/Jackdmp")

I don't know how or why it works again. Further testing by users and dev would be welcome.

oh, BTW, did you see that Solid State Logic decided to support the developpement of Ardour and [announced it this month]("http://www.solid-state-logic.com/news/ardour_news.html")...

---

### Post by MetalMusicAddict on 2006-10-29
If you want to know whats going with Ubuntu Studio look at our [WIKI]("https://wiki.ubuntu.com/UbuntuStudio") or join us on Freenode at #ubuntustudio.

---

### Post by sletz on 2006-11-02
Jackdmp is currently more for developers than end-users. Although the code is already quite stable, it does not yet implement the whole jack API and some internal behaviours are a bit different.

Concerning MP aspects, using jackdmp helps only when several applications in the jack graph can be runned at the same time, that this when the graph topology presents parallel sub-parts, for example:

1) a [input ==> A ==> B ==> C ==> output] graph is purely sequential (A, B, C have to be runned in sequence), thus jackdmp and jackd will behave the same

2) but [input ==> A ==> C ==> output] and [input ==> B ==> C ==> output] graph has "parallel" sub-parts, A and C can be runned concurently and jackdmp will behave better than jack.

I would not advice to package jackdmp in its current shape, since perfect compatibility with existing jack clients cannot be garantied, and the install step is still a bit ugly... (i know that... because i did it..:cool: )

---

### Post by sletz on 2006-11-02
oups... A and *B* can be runned at the same time...

---

### Post by damu on 2006-11-02
Thanks guys for your answers. :)

I am not sure xchat sessions are my place as I am not a dev and would probably be pretty useless. I'd rather use my limited spare time in discussing openly (forum) issues which I think matter for this new audio/multimedia distro to come, and, testing.


I guess parallel scheme is what happen in most of my configs :


'Live' set up:

-> guitar ->Jackrack-> Freewheeling -> output

-> midi guitar - synth (Zynadd, AMS, etc)-> Freewheling ->output

-> sometime, a rosegarden or Ardour session as a background soundscape ->output


'Usual' studio set up with 3 apps in sync :


-> Hydrogen -> output

-> Rosegarden ->output

-> Ardour -> output


I wonder how jackdmp handles a Rosegarden or Ardour session with synths and/or plug-ins on many tracks...I still have to try that.


I've been running another 'live' test with Jackdmp to push my config to its limits. I chose to use 2 instances of Jamin in the config as it is a very hungry processor app. :


-> ams (sequence 1) -> jamin -> output

-> ams(2) (sequence 2) -> jamin(2) -> output

-> guitar -> jackrack (5-6 plug-ins including Gverb) -> output

-> midi ->Zynadd (5 layers of sound) -> output


It worked, even though I was obviously at the limit of the system (with a latency of 23 ms - stock kernel). No crack if I was smooth on Zynadd.... ;)

That's not the kind of config that I can run with Jackd. Just for that it is worth it for me!


There are still probably some issues with an app which release is 0.58. We could say that of Freewheeling (0.5.2.a) and so many other open source apps (compiz/berryl has not been considered stable enough to be in Ubuntu Edgy, but it is part of the default install in Mandriva).

I guess it is a matter of choice and decisions in the design and the goals of a distro : to be or not to be edgy :)

I didn't encounter any issue yet with jackdmp for 'live' set up.



I am pretty sure that most of musicians with a solid DAW (ie dual or quad core) would love to have the choice of trying a jackdmp.deb (with warnings, limitations, list of compatible apps and so on) with their config to see if they can get 50 more % of power on big projects...

If ever it doesn't work, one can still go back to jackd (I have the choice in Jack to start either with jackd or jackdmp) or remove it.


I guess I read a decent amount of threads on forums in the last couple of years about DAWS. The 2 main topics that I have noticed are :


- **power** – that's mainly what Pro tools with expensive DSPs vs Nuendo/Cubase/Samplitude is about. Another expression of the hardware/optimisation concern is pc vs Mac : one of the main selling factor in the promotion of Macs is their supposed/real superiority of power( remember the adverts for the G5...'the' most powerful computer ever in the world...same stuff with core2duo now). Macs are used a lot in multimedia production and are pretty much in every professional sound studios...


- **usability** (functionalities + ergonomic)


Ubuntu is probably the closest distro as far as usability is concerned and the main audio apps are now rock solid and functional. The amount of available apps is impressive (= loads of functionalities).


Power is definitely the big ouch of all the linux-audio-distro I have used so far (64studio, STG, Musix, Ubuntu ). My best result so far is Ubuntu with jackdmp, hence my conviction that all options should be considered for power optimisation. A 64 bits environment seems also to a less extent to make a difference. I didn't manage to install jackdmp on 64Studio and didn't even try to install ubuntu64 to test it with jackdmp. Might be my next test ...

---

### Post by damu on 2006-11-07
I installed Ubuntu 64 bits. It is more responsive than with a 32 bit environnements. I managed to install all the main audio apps : Ardour, rosegarden4, jackrack, freewheeling, patchage, zynadd and other synths, jamin, ubuntustudio (such a brilliant script that makes a difference with other audio distros :) ),etc.


I didn't manage to install jackdmp on it though. Would there be an incompatibility with jackdmp and 64 bits?

---

### Post by sletz on 2006-11-08
"I didn't manage to install jackdmp on it though" 

Is it a problem at installation step or at running step? jackdmp should compile and run on 64 bits (it has been already been tested by some people on other distrib)

Could you please send me any relevant information on the problem?

Concerning jackdmp installation, i'm currently working on a less intrusive system that should allow users to easily and dynamically switch between the jackd and jackdmp.

---

### Post by nalmeth on 2006-11-08
What are you suffering as a result of jack not supporting multithreading? I'm just curious.

On my EM64T intel 3.0 GHz (not dual, but hyperthreading, treated as dual with SMP though correct?), all I had to do was tweak the jack settings, and I have low-latency, and experiencing ZERO jack runs. And thats with the 386 kernel (NVIDIA driver :rolleyes: ), Beryl, jack, ardour, JAMin, zynaddsubFX all running and working. ZERO XRUNS

So purely out of curiosity, what would multi-threading jack improve for me? I don't question that it it's valuable, and needed to make linux a more obvious answer for studio work, but I'm quite happy with the performance I'm getting. 

Thanks for reporting your experience with 64-bit though, I've been thinking about that alot lately..

---

### Post by sletz on 2006-11-08
The standard jack server always activates the graph of jack client in a purely sequential manner. jackdmp better use mp machines by scheduling jack client activation more efficienly, when possible, that is when clients can be runned in parrallel on different processor. 

Read "jack for multi-processor machines" related papers here: [http://www.grame.fr/Recherche/Publications/list/list.php?lang=fr&type=ARCH](http://www.grame.fr/Recherche/Publications/list/list.php?lang=fr&type=ARCH)

---

### Post by nalmeth on 2006-11-08
> that is when clients can be runned in parrallel on different processor.
Thanks for the link,

---

### Post by damu on 2006-11-10
Thanks Stéphane to take some time , answering in this forum :)
BTW, quel temps fait-il à Lyon 5? 

When I try to install jackdmp on Ubuntu64, I get :

> damu@damu-desktop:~/jackdmp/jackdmp_0.58/src/linux$ make
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackActivationCount.o ../common/JackActivationCount.cpp
make: g++: Command not found
make: *** [JackActivationCount.o] Error 127



Nalmeth
Only one core will be fully used in an audio environment under linux (whether you use hyperthreading or not for this core won't change anything to it).On dual or quad cores,at best, the second core will be used for gui, but the heavy work (audio processing ) is assigned to one core on linux. My system on heavy loads gives me : CPU1 :90% - CPU 2 : 5%..it takes  us years back as far as power efficiency is concerned, compared to any Mac or Win based DAW. 
Jackdmp is the answer to this issue for most of "heavy loads" configurations - ie it makes linux based DAWs a viable option on modern hardware used for DAWs.

---

### Post by sletz on 2006-11-11
g++ is simply the C++ compiler.... check its installation.

---

### Post by nalmeth on 2006-11-11
> Nalmeth
Only one core will be fully used in an audio environment under linux (whether you use hyperthreading or not for this core won't change anything to it).On dual or quad cores,at best, the second core will be used for gui, but the heavy work (audio processing ) is assigned to one core on linux. My system on heavy loads gives me : CPU1 :90% - CPU 2 : 5%..it takes us years back as far as power efficiency is concerned, compared to any Mac or Win based DAW. 
Jackdmp is the answer to this issue for most of "heavy loads" configurations - ie it makes linux based DAWs a viable option on modern hardware used for DAWs.
OK, with your CPU ratio I can see the result. As far as processing goes, or just with holding low-latency, it could make a big difference, at least when a lot of HEAVY processing is done, and multiple apps used simultaneously. 

However, I must suspect that one could get away with audio work on linux, and have the same quality product, only having taken more time to produce.

---

### Post by damu on 2006-11-11
I installed g++ with synaptic and things went further, but I got stuck again at the "make install" stage :

> damu@damu-desktop:~$ cd /home/damu/jackdmp/jackdmp_0.58/src/linux
damu@damu-desktop:~/jackdmp/jackdmp_0.58/src/linux$ make
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackActivationCount.o ../common/JackActivationCount.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAPI.o ../common/JackAPI.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAudioDriver.o ../common/JackAudioDriver.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackClient.o ../common/JackClient.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackConnectionManager.o ../common/JackConnectionManager.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackDriver.o ../common/JackDriver.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackEngine.o ../common/JackEngine.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackEngineTiming.o ../common/JackEngineTiming.cpp
cc -g -O3  -fPIC  -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o JackError.o ../common/JackError.c
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackExternalClient.o ../common/JackExternalClient.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackFrameTimer.o ../common/JackFrameTimer.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackFreewheelDriver.o ../common/JackFreewheelDriver.cpp
g++ -g -O3  -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackGlobalsServer.o ../common/JackGlobalsServer.cpp
In file included from alsa/JackAlsaDriver.h:28,
                 from ../common/JackGlobalsServer.cpp:55:
alsa/alsa_driver.h:23:28: error: alsa/asoundlib.h: No such file or directory
alsa/alsa_driver.h:61: error: ISO C++ forbids declaration of &#8216;snd_pcm_channel_area_t&#8217; with no type
alsa/alsa_driver.h:61: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:62: error: ISO C++ forbids declaration of &#8216;snd_pcm_channel_area_t&#8217; with no type
alsa/alsa_driver.h:62: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:87: error: &#8216;snd_pcm_format_t&#8217; does not name a type
alsa/alsa_driver.h:88: error: &#8216;snd_pcm_format_t&#8217; does not name a type
alsa/alsa_driver.h:94: error: ISO C++ forbids declaration of &#8216;snd_ctl_t&#8217; with no type
alsa/alsa_driver.h:94: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:95: error: ISO C++ forbids declaration of &#8216;snd_pcm_t&#8217; with no type
alsa/alsa_driver.h:95: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:96: error: ISO C++ forbids declaration of &#8216;snd_pcm_t&#8217; with no type
alsa/alsa_driver.h:96: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:97: error: ISO C++ forbids declaration of &#8216;snd_pcm_hw_params_t&#8217; with no type
alsa/alsa_driver.h:97: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:98: error: ISO C++ forbids declaration of &#8216;snd_pcm_sw_params_t&#8217; with no type
alsa/alsa_driver.h:98: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:99: error: ISO C++ forbids declaration of &#8216;snd_pcm_hw_params_t&#8217; with no type
alsa/alsa_driver.h:99: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/alsa_driver.h:100: error: ISO C++ forbids declaration of &#8216;snd_pcm_sw_params_t&#8217; with no type
alsa/alsa_driver.h:100: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
alsa/JackAlsaDriver.h:58: error: &#8216;snd_pcm_t&#8217; has not been declared
alsa/JackAlsaDriver.h:59: error: &#8216;snd_pcm_hw_params_t&#8217; has not been declared
alsa/JackAlsaDriver.h:60: error: &#8216;snd_pcm_sw_params_t&#8217; has not been declared
alsa/JackAlsaDriver.h:76: error: &#8216;snd_pcm_uframes_t&#8217; has not been declared
alsa/JackAlsaDriver.h:77: error: &#8216;snd_pcm_uframes_t&#8217; has not been declared
alsa/JackAlsaDriver.h:78: error: &#8216;snd_pcm_uframes_t&#8217; has not been declared
alsa/JackAlsaDriver.h:79: error: &#8216;snd_pcm_uframes_t&#8217; has not been declared
make: *** [JackGlobalsServer.o] Error 1
damu@damu-desktop:~/jackdmp/jackdmp_0.58/src/linux$ sudo make install
Password:
cp jackdmp /usr/local/bin
cp: cannot stat `jackdmp': No such file or directory
make: *** [install] Error 1




Nalmeth
With a  slower pc , one can take more time to deal with no "real time projects".
But an audio project which involves many apps in sync, loads of tracks and loads of plug-ins won't take longer to run on a less powerfull pc - it just won't take it, it won't run. 
An average pop-rock song may need 30 to 60 tracks (I remember the article of a sound engineer explaining how Mickael Jackson's mix would require more than 120 tracks on one of his last album!). Now , you will probably want to gate, compress, eq on most tracks, and chorus, delay, reverb on loads of them too in Ardour. You might like to run the midi part of it with synths in Rosegarden in sync, so that you can still change some things at the mix stage...I would run out of power on every project with my P IV 2.8 GHz...that's why I upgraded (I was told that linux handles well multi procs.It's true for the system ...but not for audio apps which are not multi threaded).
The issue is even more accurate for live performances!
The freedom and the way open-source/linux  opens the gates of creativity  is unique. I wouldn't go back to another system...I'd rather use jackdmp and go on ;)

---

### Post by sletz on 2006-11-12
jackdmp needs to have ALSA headers installed.
You'll have to install alsa development stuff (probaby something like 'alsa-dev' package)

---

### Post by sletz on 2006-11-12
To get the latest jackdmp SVN version, you can do:

svn co [http://subversion.jackaudio.org/jackmp/trunk/jackmp/](http://subversion.jackaudio.org/jackmp/trunk/jackmp/)

---

### Post by nalmeth on 2006-11-12
>  Nalmeth
With a  slower pc , one can take more time to deal with no "real time projects".
But an audio project which involves many apps in sync, loads of tracks and loads of plug-ins won't take longer to run on a less powerfull pc - it just won't take it, it won't run. 
An average pop-rock song may need 30 to 60 tracks (I remember the article of a sound engineer explaining how Mickael Jackson's mix would require more than 120 tracks on one of his last album!). Now , you will probably want to gate, compress, eq on most tracks, and chorus, delay, reverb on loads of them too in Ardour. You might like to run the midi part of it with synths in Rosegarden in sync, so that you can still change some things at the mix stage...I would run out of power on every project with my P IV 2.8 GHz...that's why I upgraded (I was told that linux handles well multi procs.It's true for the system ...but not for audio apps which are not multi threaded).
The issue is even more accurate for live performances!

120 tracks!! Insane
Another note though, slower PC's won't have multi threading processors would they? An upgrade would be required anyway to get decent performance. In any case, I suppose if you want true power performance you have to get your hands dirty, no matter what.
I'm keeping this thread bookmarked, I want to try this jackdmp later this week. Seemingly something I will have to conquer eventually if I want to get anywhere. 
Mind you, I don't plan on making cheesy pop-music, and I sure as hell ain't making a song with 120 tracks. 
OK, maybe once, for fun, it would be a thriller. 
:rolleyes:
>  The freedom and the way open-source/linux opens the gates of creativity is unique. I wouldn't go back to another system...I'd rather use jackdmp and go on :wink:
Cheers to that!

---

### Post by damu on 2006-11-24
I gave up for the installation on 64 bits. Couldn't find the alsa dependencies in synaptic, or they wouldn't install for some reasons. 
However, VST support, which I need in my DAW, is only possible in 32 bits on linux(I thought there might be a possibility with chmod but it seems nobody cracked it yet) , so I went back to 32 bits...

I installed the new version of jackdmp :[jackdmp_0.59]("http://www.grame.fr/~letz/jackdmp.html").

However , when I can't start jack with jackdmp, I get
> 
00:04:33.571 Patchbay deactivated.
00:04:33.602 Statistics reset.
00:04:33.668 Startup script...
00:04:33.669 artsshell -q terminate
00:04:33.690 MIDI connection graph change.
can't create mcop directory
Creating link /home/damu/.kde/socket-ubuntu.
00:04:33.925 Startup script terminated with exit status=256.
00:04:33.925 JACK is starting...
00:04:33.925 jackdmp -R -dalsa -dhw:0 -r44100 -p512 -n2
00:04:33.927 JACK was started with PID=5192 (0x1448).
jackdmp: error while loading shared libraries: libjackdmp.so: cannot open shared object file: No such file or directory
00:04:33.929 JACK was stopped with exit status=127.
00:04:34.128 MIDI connection change.
00:04:36.172 Could not connect to JACK server as client. Please check the messages window for more info.

How could I go round this one? 

Thanks,

---

### Post by sletz on 2006-11-25
This seems like an compilation or installation problem. Can you publish the result of : make clean && make && sudo make install done again in the "Linux" folder?
After installation, you can also try to launch the server in a terminal using the: jackdmp -R -d alsa command.

---

### Post by damu on 2006-11-25
I did it twice with the same result that I had in the first place. The first time, I did make clean, make, make remove (to make sure the previous installation wouldn't interfere), sudo make install.

The second time, I just did the sequence you gave me : make clean, make, sudo make install :
> damu@ubuntu:~/jackdmp/jackdmp_0.59/src/linux$ make clean
rm -f *.o
rm -f jackdmp  libjackdmp.so libjackmp.so libjackwrapper.so jack_alsa.so jack_dummy.so \
                synchroClient synchroServer synchroServerClient testSem jack_test
damu@ubuntu:~/jackdmp/jackdmp_0.59/src/linux$ make
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackActivationCount.o ../common/JackActivationCount.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAPI.o ../common/JackAPI.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAudioDriver.o ../common/JackAudioDriver.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackClient.o ../common/JackClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackConnectionManager.o ../common/JackConnectionManager.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackDriver.o ../common/JackDriver.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackEngine.o ../common/JackEngine.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackEngineTiming.o ../common/JackEngineTiming.cpp
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o JackError.o ../common/JackError.c
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackExternalClient.o ../common/JackExternalClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackFrameTimer.o ../common/JackFrameTimer.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackFreewheelDriver.o ../common/JackFreewheelDriver.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackGlobalsServer.o ../common/JackGlobalsServer.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackGraphManager.o ../common/JackGraphManager.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackInternalClient.o ../common/JackInternalClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackPort.o ../common/JackPort.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackPosixSemaphore.o ../common/JackPosixSemaphore.cpp
../common/JackPosixSemaphore.cpp:118:2: warning: #warning JackPosixSemaphore::TimedWait not available : synchronous mode may not work correctly if POSIX semaphore are used
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackPosixThread.o ../common/JackPosixThread.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackFifo.o ../common/JackFifo.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackLoopbackDriver.o ../common/JackLoopbackDriver.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackServer.o ../common/JackServer.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackShmMem.o ../common/JackShmMem.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackThreadedDriver.o ../common/JackThreadedDriver.cpp
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o shm.o ../common/shm.c
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackSocket.o ../common/JackSocket.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackSocketServerChannel.o ../common/JackSocketServerChannel.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackSocketNotifyChannel.o ../common/JackSocketNotifyChannel.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackSocketServerNotifyChannel.o ../common/JackSocketServerNotifyChannel.cpp
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o JackTime.o ../common/JackTime.c
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackServerAPI.o ../common/JackServerAPI.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackGlobals.o ../common/JackGlobals.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackDriverLoader.o ../common/JackDriverLoader.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o internal_metro.o ../example-clients/internal_metro.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackDebugClient.o ../common/JackDebugClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackTransportEngine.o ../common/JackTransportEngine.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackServerGlobals.o ../common/JackServerGlobals.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   -shared JackActivationCount.o JackAPI.o JackAudioDriver.o JackClient.o JackConnectionManager.o JackDriver.o JackEngine.o JackEngineTiming.o JackError.o JackExternalClient.o JackFrameTimer.o JackFreewheelDriver.o JackGlobalsServer.o JackGraphManager.o JackInternalClient.o JackPort.o JackPosixSemaphore.o JackPosixThread.o JackFifo.o  JackLoopbackDriver.o JackServer.o JackShmMem.o JackThreadedDriver.o shm.o JackSocket.o JackSocketServerChannel.o  JackSocketNotifyChannel.o JackSocketServerNotifyChannel.o JackTime.o JackServerAPI.o JackGlobals.o JackDriverLoader.o internal_metro.o JackDebugClient.o  JackTransportEngine.o JackServerGlobals.o -lpthread -lrt -lasound  -o libjackdmp.so
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o ringbuffer.o ../common/ringbuffer.c
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackGlobalsClient.o ../common/JackGlobalsClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackLibClient.o ../common/JackLibClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackLibAPI.o ../common/JackLibAPI.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackSocketClientChannel.o ../common/JackSocketClientChannel.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   -shared JackActivationCount.o JackAPI.o JackClient.o JackConnectionManager.o ringbuffer.o JackError.o JackFrameTimer.o JackGlobalsClient.o JackGraphManager.o JackLibClient.o JackLibAPI.o JackPort.o JackPosixSemaphore.o JackFifo.o JackPosixThread.o JackShmMem.o shm.o JackSocket.o JackSocketClientChannel.o JackTime.o JackGlobals.o JackDebugClient.o JackTransportEngine.o   -lpthread -lrt -lasound   -o libjackmp.so
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAPIWrapper.o ../common/JackAPIWrapper.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   -shared JackAPIWrapper.o ringbuffer.o -o libjackwrapper.so
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o Jackdmp.o ../common/Jackdmp.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa    Jackdmp.o  -lpthread -lrt -lasound  libjackdmp.so -o jackdmp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackAlsaDriver.o alsa/JackAlsaDriver.cpp
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o memops.o alsa/memops.c
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o generic_hw.o alsa/generic_hw.c
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o hdsp.o alsa/hdsp.c
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o hammerfall.o alsa/hammerfall.c
cc -g -O3 -fPIC -DUSE_POSIX_SHM -I../common -I../tests -I../example-clients -Ialsa    -c -o ice1712.o alsa/ice1712.c
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   -shared JackAlsaDriver.o memops.o generic_hw.o hdsp.o hammerfall.o ice1712.o -lpthread -lrt -lasound  libjackdmp.so  -o jack_alsa.so
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackDummyDriver.o ../common/JackDummyDriver.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   -shared JackDummyDriver.o   -lpthread -lrt -lasound  libjackdmp.so  -o jack_dummy.so
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o testSynchroClient.o ../tests/testSynchroClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   JackPosixSemaphore.o testSynchroClient.o JackPosixThread.o JackError.o JackFifo.o -lpthread -lrt -lasound  -o synchroClient
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o testSynchroServer.o ../tests/testSynchroServer.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   JackPosixSemaphore.o testSynchroServer.o JackPosixThread.o JackError.o JackFifo.o -lpthread -lrt -lasound  -o synchroServer
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o testSynchroServerClient.o ../tests/testSynchroServerClient.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o JackPthreadCond.o ../common/JackPthreadCond.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   JackPosixSemaphore.o testSynchroServerClient.o JackPosixThread.o JackError.o JackFifo.o JackShmMem.o shm.o JackPthreadCond.o -lpthread -lrt -lasound  -o synchroServerClient
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o testSem.o ../tests/testSem.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   JackPosixSemaphore.o testSem.o JackPosixThread.o JackError.o JackFifo.o -lpthread -lrt -lasound  -o testSem
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa     -c -o jack_test.o ../tests/jack_test.cpp
g++ -g -O3 -fPIC -DSOCKET_RPC_FIFO_SEMA -D__SMP__ -DADDON_DIR=\"/usr/local\"  -I../common -I../tests -I../example-clients -Ialsa   jack_test.o -L. -ljackmp -o jack_test
damu@ubuntu:~/jackdmp/jackdmp_0.59/src/linux$ sudo make install
cp jackdmp /usr/local/bin
cp libjackmp.so /usr/local/lib
cp libjackdmp.so /usr/local/lib
install -d /usr/local/lib/jackmp/
cp jack_alsa.so /usr/local/lib/jackmp
cp jack_dummy.so /usr/local/lib/jackmp
cd /usr/local/lib && [ -f libjack.so.0.0.23 ] && mv -f libjack.so.0.0.23 tmp_libjack.so.0.0.23 || echo "Jack not found, continue..."
Jack not found, continue...
cd /usr/local/lib && rm -f libjack.so*
cd /usr/local/lib && ln -s libjackmp.so  libjack.so
cd /usr/local/lib && ln -s libjackmp.so  libjack.so.0
/sbin/ldconfig
damu@ubuntu:~/jackdmp/jackdmp_0.59/src/linux$ 


The result in Jack is : 
> 21:07:59.751 Patchbay deactivated.
21:07:59.764 Statistics reset.
21:07:59.838 MIDI connection graph change.
21:07:59.978 MIDI connection change.
21:08:12.953 Startup script...
21:08:12.953 artsshell -q terminate
can't create mcop directory
Creating link /home/dominique/.kde/socket-ubuntu.
21:08:13.190 Startup script terminated with exit status=256.
21:08:13.190 JACK is starting...
21:08:13.190 jackdmp -R -dalsa -dhw:2 -r44100 -p512 -n2
21:08:13.192 JACK was started with PID=22627 (0x5863).
jackdmp: error while loading shared libraries: libjackdmp.so: cannot open shared object file: No such file or directory
21:08:13.197 JACK was stopped with exit status=127.
21:08:15.375 Could not connect to JACK server as client. Please check the messages window for more info.

Thanks for your help :)

---

### Post by sletz on 2006-11-26
As you can see the "install" script just copy jackdmp and associated libraries in /usr/local location. You can type: ldd jackdmp to check what libraries the executable is going to use. You should see that "jackdmp" uses "libjackdmp.so" that is actually located in /usr/local/lib. 
Can you check that? Can you try to start jackdmp in a terminal (not with qjackctl)? Does the 0.58 install correctly on the same machine?

---

