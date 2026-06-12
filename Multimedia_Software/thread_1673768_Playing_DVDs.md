---
title: "Playing DVDs"
date: 2011-01-22
forum: Multimedia Software
---

### Post by TimmyK. on 2011-01-22
Hello all. I have a Dell laptop running Ubuntu. I tried to play a DVD on the Movie Player, but this did not work. So I downloaded VLC. However, when I tried to play the DVD there, it says it is playing it for about a second (the whole time there is nothing showing in the player), and then it stops. I have no idea what the problem is. VLC plays everything else fine (music, audio, and AVI files). And I know I am doing everything right; I went to the Help page and carefully followed all the instructions. I would be grateful for anyone who can fix this. Thanks in advance.

---

### Post by kitchenguy on 2011-01-22
As I understand it Ubuntu does not ship with the codecs to play a DVD because there are licence issues.

If you go into the "Synaptic Package Manager" (Under System --> Administration) and type "restricted" in the search box you will find a package called Ubuntu Restricted extras.

You may need to enable the third party repositories and refresh your software list as well.  This is in Synaptic under Settings --> Repositories  Other Software tab.


That has the codecs and a bunch of other stuff.  You can also go to the Medibuntu webpage and add their repositories and get games, stuff etc

---

### Post by TimmyK. on 2011-01-23
No ,just check out the VLC website. It can play DVDs. I just keep having this problem. There is not error message or anything.

---

### Post by kitchenguy on 2011-01-23
VLC will certainly play just about everything, but you do need the codecs.  If you open a terminal and type: 
sudo apt-get install ubuntu-restricted-extras

There is an explanation of all this here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


That should do the trick.

---

### Post by TimmyK. on 2011-01-23
How do you set the region on VLC then? I think that may be the problem.

---

### Post by I'mGeorge on 2011-01-23
VLC or Xbmc

---

### Post by johntaylor1887 on 2011-01-23
> **TimmyK. said:**
> No ,just check out the VLC website. It can play DVDs. I just keep having this problem. There is not error message or anything.

VLC that is in the ubuntu repos does not play DVD's out of the box. You will need to install libdvdcss2 first. VLC for windows, however, does play DVD's.

---

### Post by Oscareightyone on 2011-01-23
TimmyK, if you don't listen to what people say, they will never solve your problem.

---

### Post by TimmyK. on 2011-01-23
@Oscareightyone: Um... yes, I know.

@Johntaylor1887: So in other words, VLC can play DVDs if you install libdvdcss2? Were do I install it from?

---

### Post by rocthrttle on 2011-01-23
copy and paste "libdvdcss2" into ubuntu software center

it should come up. install it. also other tech guys try to use the ubuntu software center with the newbies it's less confusing/scary then the terminal or synaptic package manager.

---

### Post by TimmyK. on 2011-01-23
OK, only one thing I need to do still. I know this may sound stupid to most Ubuntu veterans, but how do I get to either Synaptic or command line?

---

### Post by TimmyK. on 2011-01-23
I already posted a reply, but it didn't appear anywhere. To install libdvdread2, I have to go to Synaptic or command line. How do I get here? Is this the Command Prompt of Ubuntu? And please give me simple instructions (e.g. "Go to 'places'..." that sort of thing); this is only me second day with Ubuntu and so I will not be familiar with most of the places and folders.

---

### Post by BicyclerBoy on 2011-01-24
Study this webpage & associated links..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This is the best place to start.

If you do not understand synaptic/apt package management then read this..
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

The Ubuntu website is a excellent source of info.

---

### Post by kitchenguy on 2011-01-24
Hi Timmy,

Sorry if you were confused, it is a little overwhelming at first and it is easy to forget I was there three years ago.  Ubuntu really is a good system and if you stick with it you will find it useful - it's also free. You may find it annoying it times trying to get it to do stuff (like play a DVD!) but that can be half the fun.

Start with the software centre. There is a menu titled "Applications" click on it and select "Ubuntu Software Centre" an image of my desktop is attached (screenshot.jpg) showing what you will get.  Type "restricted" into the search box and you should get the same search result as me.

Click on "Ubuntu Restricted extras" this will highlight it and click Install - attached is install.jpg image (note mine says remove because I already have it, yours will say Install.

If you do not see that package, then you need to set your software sources.   This is simply telling the computer where to get the software from.  For example with other systems you drive to a store and buy some software - with Ubuntu you simply tell it where they are giving the software away from and it goes and gets it.

Click on Edit and choose Software Sources at the bottom.  Choose the Other Software tab and tick the boxes of all the sources that are not ticked.  See the attached Sources.jpg.  Note yours will look different because mine has several sources added.

Then click reload and go back to entering Restricted in the search box.

Now, there is a different and easier way to do this - but sometimes people get put off by it, but using the terminal is very powerful.

Simply Click on "Applications --> Accessories --> Terminal"  This will bring up the command Line Interface (CLI).  simply cut and paste this into the window at the prompt:

sudo apt-get install ubuntu-restricted-extras

It will then ask for your password and go and do its thing.

I really hope this works for you man - stay cool and stick with it.  Remember that it is FREE!

---

### Post by mmsmc on 2011-01-24
not only is it free its the best, thanks for the posts this also helped me

---

### Post by rocthrttle on 2011-01-24
> **TimmyK. said:**
> I already posted a reply, but it didn't appear anywhere. To install libdvdread2, I have to go to Synaptic or command line. How do I get here? Is this the Command Prompt of Ubuntu? And please give me simple instructions (e.g. "Go to 'places'..." that sort of thing); this is only me second day with Ubuntu and so I will not be familiar with most of the places and folders.


also dont be afraid to mess around and explore. just do a backup first. like the guy said linux is the best platform but it is going to take some getting used to. my favorite analogy is "you can drive a car right? so it's like driving in europe. just get used to driving on the other side of the road." linux is like driving on the other side. just different is all.

for a backup use dejadup found in the ubuntu software center.

---

### Post by TimmyK. on 2011-01-25
Don't get me wrong, I love Linux! I don't see why anyone would *pay* for Windows when they could get Linux for free.

However, when I click install, it says I must first remove Ffmpeg codec library (Libavcodec52) and Ffmpeg utility library (Libavutil50). What are these, and are they safe to remove?

---

### Post by BicyclerBoy on 2011-01-25
Yes that is okay, the new packages replace the exising libavformat codec utils etc..

The libavfilter,codec,format,utils are libraries from ffmpeg project.

The standard *buntu ones are stripped of non-free copyrighted stuff.
You are replacing these with the unstripped/complete version..
These libraries are shared system files used by any app that dynamically loads the system libs.

---

### Post by TimmyK. on 2011-01-25
I installed it, but it I still have the same problem. Maybe it is because I haven't set the region code? How do I do this?

---

### Post by rocthrttle on 2011-01-25
[http://tinyurl.com/6awosko](http://tinyurl.com/6awosko)

go here

---

### Post by TimmyK. on 2011-01-25
OK, I installed regionset. Now were do I go to use it?

---

### Post by rocthrttle on 2011-01-25
can you be a little bit more specific. 'cause i'm confused now. what? once it is set it should be set for any and all programs i would think. did you try to play something?

---

