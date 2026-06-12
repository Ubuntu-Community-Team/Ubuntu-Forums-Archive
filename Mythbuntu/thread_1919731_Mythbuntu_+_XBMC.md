---
title: "Mythbuntu + XBMC"
date: 2012-02-03
forum: Mythbuntu
---

### Post by efid845 on 2012-02-03
Hi!
I have a old PC,and want to install on it Mythbuntu.
But,i want to use XBMC too.
How can i install XBMC on Mythbuntu?

thanks

---

### Post by nickrout on 2012-02-03
Same as you would on any other ubuntu machine. 

```
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc

```

If you want to start it from within mythtv (which is what I do) then add a menu entry:

```
cp /usr/share/mythtv/themes/defaultmenu/library.xml ~/.mythtv/
```

Then edit ~/.mythtv/library.xml to include the following:

```
<button>
                <type>XBMC</type>
                <text>XBMC</text>
                <description>Launch XBMC</description>
                <action>EXEC /usr/bin/xbmc</action>
        </button>
```

Then in your Media Library menu there will be an entry for XBMC.

---

### Post by lionsnob on 2012-04-22
Nick -

Thanks.  This works great for me in 0.25.  Having MythTV and XBMC on the same HTPC makes for one nice experience!

Steve

---

### Post by andree_b on 2012-04-23
Out of curiosity:
What does XBMC better than the corresponding Myth components?
Or what additional features do you get with XBMC?

Never used XBMC yet and I wonder if i miss something there.

---

### Post by klc5555 on 2012-04-23
XBMC tends to be a superior option for the organizing and playback of most video content. I haven't used mythvideo in nearly a year since integrating XBMC into my mythtv network. Video add-ons also extend XBMC into quite a few areas of internet video content, if they are things you use. If you prefer XBMC as your primary video interface to mythtv, there is also a well-integrated mythfrontend video add-on (for 0.23.x and 0.24.x), but I find the arrangement of elements a bit odd and so continue to use mythfrontend as the primary interface rather than XBMC.

XBMC is also a superior option for organizing and playing back music content from a media center, and I rely upon it for that.

---

### Post by nickrout on 2012-04-29
> **klc5555 said:**
> XBMC tends to be a superior option for the organizing and playback of most video content. I haven't used mythvideo in nearly a year since integrating XBMC into my mythtv network. Video add-ons also extend XBMC into quite a few areas of internet video content, if they are things you use. If you prefer XBMC as your primary video interface to mythtv, there is also a well-integrated mythfrontend video add-on (for 0.23.x and 0.24.x), but I find the arrangement of elements a bit odd and so continue to use mythfrontend as the primary interface rather than XBMC.

XBMC is also a superior option for organizing and playing back music content from a media center, and I rely upon it for that.

I would mostly agree with that, but mythvideo gets better all the time. The necessity to follow fairly rigid naming rules for mythvideo if you want decent metadata  is the most annoying thing.

---

### Post by superm1 on 2012-04-29
It's worth noting that XBMC is directly available in 12.04 now.  So no need to muck with their PPA if you are on 12.04.

---

### Post by MOGuy78 on 2012-05-04
I'm trying to decide myself which would be a better fit to use with Mythbuntu, XBMC or MediaTomb.
Overall, would most choose XBMC over MediaTomb?

---

### Post by nickrout on 2012-05-04
> **MOGuy78 said:**
> I'm trying to decide myself which would be a better fit to use with Mythbuntu, XBMC or MediaTomb.
Overall, would most choose XBMC over MediaTomb?

What is it you want to do? Why do you need either if you have mythtv?

---

### Post by MOGuy78 on 2012-05-05
Sorry, I guess I didn't explain what I'm wanting to do.
I've just installed an Ubuntu Server and was going to use it as a media server.
I have a Hauppauge TV card installed and I was planning on using the MythTV backend to record my selected TV shows,
and then use the other (either XBMC or MediaTomb) as the frontend to watch those shows from on my other computers.

Is this not right?

---

### Post by klc5555 on 2012-05-05
If you've decided to use one of these media-center apps as your primary user interface (rather than mythfrontend), the current XBMC 11.0 already has a video plugin ("Mythbox") that acts as a well-integrated frontend from within XBMC for a mythtv backend (0.23, 0.24, and even 0.22: I don't know yet how well it works with 0.25). In this case your remote frontends with XBMC would not need actual Mythtv installed on them at all. I'm not certain MediaTomb has an equally well-developed interoperability with mythtv backends.

---

### Post by nickrout on 2012-05-05
> **MOGuy78 said:**
> Sorry, I guess I didn't explain what I'm wanting to do.
I've just installed an Ubuntu Server and was going to use it as a media server.
I have a Hauppauge TV card installed and I was planning on using the MythTV backend to record my selected TV shows,
and then use the other (either XBMC or MediaTomb) as the frontend to watch those shows from on my other computers.

Is this not right?

I have not used mediatomb but my reading of their website shows that i is a media server program.

The correct way to do what you want is to install mythtv on the other computers and use mythfrontend to watch the shows. Simple really.

Oh and mythbox does not work with an 0.25 backend.

---

### Post by klc5555 on 2012-05-06
"Correct" is a little harsh. As usual, it all depends on what the OP wants to do. If he wants to center his media system on TV recording and playback with occasional forays into other media, then of course you're right. That's what mythtv was written to do. And that's the arrangement that most of us on this forum use.

If, however, the OP wishes to base his media center on media other than TV recording and playback, but allow still for occasional television, then XBMC + mythbox addon may be a better solution for him. There was obviously a need for such an arrangement, that's why the addon was written and continues to be actively maintained.

---

### Post by nickrout on 2012-05-06
> I have a Hauppauge TV card installed and I was planning on using the MythTV backend to record my selected TV shows,
and then use the other (either XBMC or MediaTomb) as the frontend to watch those shows from on my other computers.

So yes, playing back recordings is what he wants to do.

mythbox does not currently work with 0.25, which leaves little alternative to mythtv.

---

### Post by klc5555 on 2012-05-06
[> **nickrout said:**
> So yes, playing back recordings is what he wants to do.

mythbox does not currently work with 0.25, which leaves little alternative to mythtv.

Except ... maybe ... Mythtv 0.24.  MOGuy78 said he installed "an Ubuntu Server". He didn't say "Mythbuntu", he didn't say "12.04", he didn't say "with Mythtv 0.25". If he has installed any of the other currently supported Ubuntu versions --10.04 LTS, 10.10, 11.04, 11.10 --he'll be by default running Mythtv 0.24, and can, _if he so desires_ , run mythbox for the few weeks until it is updated for 0.25. He might even wish to keep his mythbackend on the more mature 0.24 until 0.25 gets the normal new version bugs shaken out of it to the tune of 0.25.1 He might even like the Mythtv 0.24 backend enough to keep it with later versions of his "Ubuntu server". His choice. 
  
Nor did MOGuy78 say what sort of frontend machines he wanted to run to connect to his mythbackend. Depending on what those are, the XBMC + addon may still make more sense, as he might have an easier time with XBMC on his iOS device or Windows machine (or even the Windows Mythtv viewer in the latter case) than he will have getting a standard mythfrontend running. He may be pleased that he can be less concerned with protocol mismatch than he would be running a standard mythfrontend. (On the other hand, for his Android thingies MOGuy78 will use the mythfrontend for Android, which is supposed to run just as well or as badly on 0.25 as it does on 0.23.x-0.24)

So the bottom line is, MOGuy78 may find a plain vanilla Mythtv 0.25 mythbackend/multiple Linux mythfrontend setup like 90% of us on this forum use to be ideal. Great. But if he wants or needs a different setup, there is more than enough flexibility available to him to achieve a reasonable alternative solution. His choice is not simply between "correct" and caustic dismissal.

---

### Post by MOGuy78 on 2012-05-12
Thanks for all of the feedback so far.  I'm using Ubuntu Server 10.04LTS.  I figured that I should use it since it has been around for awhile and should have most of the kinks taken out by now.
My plan was to put MythTV on my server as a backend to record shows/movies on to it, then watch them from other computers.  Do I even need to use a frontend on the server?

The method I was going to use for installing MythTV was to type "sudo apt-get install mythtv" in to the CLI, then type "mythtv-setup" to configure it.  I don't know what version of the program this will install, though.

After that, I would probably use something such as XBMC to view the media from other computers.  Does this sound reasonable?

---

### Post by klc5555 on 2012-05-12
> **MOGuy78 said:**
> Thanks for all of the feedback so far.  I'm using Ubuntu Server 10.04LTS.  I figured that I should use it since it has been around for awhile and should have most of the kinks taken out by now.
My plan was to put MythTV on my server as a backend to record shows/movies on to it, then watch them from other computers.  Do I even need to use a frontend on the server?

The method I was going to use for installing MythTV was to type "sudo apt-get install mythtv" in to the CLI, then type "mythtv-setup" to configure it.  I don't know what version of the program this will install, though.

After that, I would probably use something such as XBMC to view the media from other computers.  Does this sound reasonable?


Sounds basically fine. Maybe a few notes, though. 10.04 will install mythtv 0.23 by default. This is certainly good enough.

If your Ubuntu server is going to be a pure mythtv backend with no frontend, you can install the entire mythtv apparatus the way you intend, (and in fact this might be better) but you really need only two packages via apt-get, synaptic, or downloading straight from packages.ubuntu.com: the package mythtv-common and the package mythtv-backend (and the dependencies they drag with them). Your method of sudo mythtv-setup will get the job done with regard to setting up. Be sure to have set up this server with a static IP address (or have your router always assign the same address to this server). Make sure that this IP address is used in the General backend setup, not localhost or 127.0.0.1 See the backend config section of the manual at:  [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

It might be easier (but not necessary) to install the whole mythtv enchilada (i.e. mythtv-common, mythtv-backend, mythtv-frontend) including the frontend on your server because sometimes it's simpler to troubleshoot a newly set up backend if you can observe a tv signal right on that machine. Once the remote machines are set up, mythfrontend never need be run on the server again.

Since your backend is intended for remote connections only, mysql must be configured to allow remote connections. In mythbuntu proper this would be done from the mythbuntu control centre, but otherwise this can be done by editing two lines in your my.cnf file in the /etc directory. The line ```
skip-networking
``` must be remarked out, so ```
# skip-networking
``` 

And mysql must be bound to the server's ip address, so a line must be added: ```
bind-address = [whatever the machine's static ip is]
``` Omit the square brackets in your actual bind-address line, of course.

And the database should be ready for remote connections once the mysql service is restarted.


Now, if you run standard mythfrontends as the remote frontends, they will need to be at the same version of mythtv as the backend, or connection will fail with a "protocol mismatch" error. So in this case 0.23 If the frontends are running Ubuntu, these frontend machines would need the two packages mythtv-frontend and mythtv-common (plus dependencies). You configure the remote frontend by typing "mythfrontend" at a prompt, and adding the necessary data when the config screens come up. The Ubuntu on the frontend machines (if it is Ubuntu) will need to also be 10.04, or if a later version, you'll need to backlevel the its mythtv packages to the 0.23 level (or update the mythtv on the server to the same level as that on the frontends --you get the idea).  

If you intend to use XBMC+mythbox as your remote frontend (it should be the current version 11.0 Eden), you will not need to worry about protocol mismatch with your mythtv 0.23 server. Your only concern will be running some OS that v. 11.0 of XBMC will install and run on. The mythbox addon connects to backends running anything from mythtv 0.22 through 0.24 You'll configure the addon by supplying the same connection information about your myth backend that you would have supplied for a conventional mythfrontend. The XBMC shell is a tad more resource-intensive than a standard Mythfrontend shell, so that if your frontend hardware is marginal, good HD playback will be a bit trickier to achieve. (Remote frontends are all about network speed, CPU, and video cards --which latter should be a currentish NVidia or at worst a good ATI)

Have fun!

---

### Post by nickrout on 2012-05-12
If you want a backend then the package to install is mythtv-backend. 

xbmc's mythbox addon will work against backends upto and including 0.24. But IMHO you are better with simply installing mythtv-frontend on the computers where you want to watch.

---

### Post by MOGuy78 on 2012-05-13
I was planning on using XBMC as my frontend, mostly because my sister and parents both use windows and the computer I use most
is a Mac.  I'm wanting a frontend that can run on both OS's, and XBMC is the only one that I know of.

---

### Post by nickrout on 2012-05-13
> **MOGuy78 said:**
> I was planning on using XBMC as my frontend, mostly because my sister and parents both use windows and the computer I use most
is a Mac.  I'm wanting a frontend that can run on both OS's, and XBMC is the only one that I know of.

mythtv works on linux OSX and windows.

---

### Post by docmichael on 2012-08-23
I just installed Mythbuntu and couldn't find xbmc on there,can someone tell me where it is located.Just learning how to do this in the last few months.
Many thanks!

---

### Post by nickrout on 2012-08-23
> **docmichael said:**
> I just installed Mythbuntu and couldn't find xbmc on there,can someone tell me where it is located.Just learning how to do this in the last few months.
Many thanks!
```
sudo apt-get install xbmc
```

Then you need to add a menu item. 

```
mv /usr/share/mythtv/themes/defaultmenu/library.xml ~/.mythtv
```

Then edit ~/.mythtv/library.xml to add a button to start xbmc

```
 <button>
                <type>XBMC</type>
                <text>XBMC</text>
                <description>Launch XBMC</description>
                <action>EXEC /usr/bin/xbmc</action>
        </button>
```

Then in mythfrontend you can find a button to start xbmc.

---

### Post by docmichael on 2012-08-23
I thought it was already in mythbunu 12.04? So the first 2 steps can be done in terminal or can i do them all in terminal? I can use putty from another machine if that would be better.

---

### Post by anonymousdog on 2012-08-23
You can do all of that in the console/terminal/text session of your choice.

---

### Post by nickrout on 2012-08-23
> **docmichael said:**
> I thought it was already in mythbunu 12.04? So the first 2 steps can be done in terminal or can i do them all in terminal? I can use putty from another machine if that would be better.

You might be thinking of the fact that as from 12.04 XBMC is in the ubuntu/mythbuntu repositories, but that doesn't mean that it is included in mythbuntu by default. 

Oh and my mv (move) command above should have been copy (cp). sorry about that.

Do it all in a terminal. You can do that one of three ways:

1. on the desktop choose the applications menu, accessories, terminal; or

2. At the desktop press ctrl-alt-f1 and log in at the console; or

3. from another computer ssh in to your mythtv box.

---

### Post by docmichael on 2012-08-23
Thanks for help! I got it set up,except for getting sound to work in xbmc.Sound works in mythbuntu. I have HDMI from a Jetway mini top PC. Doing more research on that.

---

### Post by nickrout on 2012-08-23
This isn't an xbmc support forum, but I think you need to go to Main Menu|System|System|Audio Output and set to HDMI. Perhaps you need to set audio output device too. The other settings (for Speaker configuration, downmix and receiver capabilities etc) will depend on your setup.

---

### Post by docmichael on 2012-08-24
Oh i know that this isn't an xbmc support forum,i was just commenting on how things worked out and appreciate the help!

---

### Post by tapsevarg on 2012-09-18
I have a question and this seems like the right place to ask it.

Basically, I am going to have a network featuring a total of two units. One will be a simple media player type machine (Roku, game system, etc). The other will serve as a back end/front end--this is the unit of discussion.

Now for the question. So I am trying to figure out how to configure this unit. It will be used for recording OTA TV (mythTV), a server and storing audio/video, and act as a front end. Now both MythTV and XBMC have Ubuntu flavored distros, and each could also be added on to another distro.

So which flavor would be the better option to build the system upon? Thanks

---

### Post by nickrout on 2012-09-18
XBMC does not record TV so that only leaves you one choice :)

---

### Post by crbnrod on 2012-09-23
> **nickrout said:**
> ```
sudo apt-get install xbmc
```

Then you need to add a menu item. 

```
mv /usr/share/mythtv/themes/defaultmenu/library.xml ~/.mythtv
```

Then edit ~/.mythtv/library.xml to add a button to start xbmc

```
 <button>
                <type>XBMC</type>
                <text>XBMC</text>
                <description>Launch XBMC</description>
                <action>EXEC /usr/bin/xbmc</action>
        </button>
```

Then in mythfrontend you can find a button to start xbmc.

I don't know if it's just me, but when I had XBMC start this way, I found mythfrontend was still accepting remote control keypresses, which occasionally resulted in the frontend playing a recording while I was doing whatever (usually music) in xbmc. 
I suppose there would also be a possibility of deleting a recording or changing settings via what amounts to randomly pressing navigation buttons. Is there a way to stop mythfrontend from accepting keypresses while xbmc is running "over" it?
I originally had this fixed with a couple simple scripts to kill the frontend and/or xbmc when I wanted to start the other, but after a bit I started getting ICE errors and such (which may not have been related, I don't think I ever got to the bottom of it other than stopping using xbmc for the time being).

---

### Post by nickrout on 2012-09-23
> **crbnrod said:**
> I don't know if it's just me, but when I had XBMC start this way, I found mythfrontend was still accepting remote control keypresses, which occasionally resulted in the frontend playing a recording while I was doing whatever (usually music) in xbmc. 
I suppose there would also be a possibility of deleting a recording or changing settings via what amounts to randomly pressing navigation buttons. Is there a way to stop mythfrontend from accepting keypresses while xbmc is running "over" it?
I originally had this fixed with a couple simple scripts to kill the frontend and/or xbmc when I wanted to start the other, but after a bit I started getting ICE errors and such (which may not have been related, I don't think I ever got to the bottom of it other than stopping using xbmc for the time being).

I have never experienced that problem so no suggestions

---

### Post by dgray_from_dc on 2013-07-31
Although this thread is a little stale, I have a question for my setup.

I installed Mythbuntu for use as a primary backend for my media network with multiple XBMC 12.2 clients running on Windows and Linux PCs and Android tablets and phones.  There's literally no screen in my home where I **can't** view my media!!  I'm also using the backend machine as an SMB server for a rather extensive pre-existing collection of movies and TV shows.  My backend works beautifully, my XBMC machines are able to play back my existing content via SMB and seemlessly watch live TV provided by mythbackend.

In an effort to centralize as much as I can and elliminate multiple databases on my clients, I want to share my XBMC libraries using [this guide]("http://wiki.xbmc.org/index.php?title=HOW-TO:Share_libraries_using_MySQL") from the XBMC wiki.  Due to my lack of knowledge in using MySQL, my concern is whether or not sharing XBMC data will affect any of the MythTV databases.

Any thoughts?

---

