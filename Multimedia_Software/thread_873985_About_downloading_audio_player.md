---
title: "About downloading audio player"
date: 2008-07-29
forum: Multimedia Software
---

### Post by ornovscot on 2008-07-29
Hi.

I am rather new to Ubuntu.  I've used Windows Media Player, Winamp and Real Player.

I'm using a Dell Inspiron computer with Ubuntu.  I've never used the latter with an audio player.

I would like to listen to an Internet radio station that features Windows Media Player, Real Player and Winamp on its website.

After doing a search I found that Amarok is one of the audio players used for Ubuntu.  

How do I download this player, and would it work were I to click onto one of the audio player icons on the website of the Internet station featuring Windows Media player, etc.  

I don't want to download the audio player in such a way that I harm anything else working in the computer.


Any help would be much appreciated.

Thank you in advance.

---

### Post by pytheas22 on 2008-07-29
You can listen to Internet radio with Rhythmbox, which is already installed into Ubuntu by default.  You can find it under the Applications>Sound and Video menu.  Just open it, and under the Library section, go to Radio.  Then in the upper-right portion of the screen, you'll see a button called "New Internet Radio Station."  Click there, enter the URL of the station you want, and voilà.

You could also use Movie Player I believe to listen to radio if you want something that looks more like Windows Media Player (Rhythmbox is more like iTunes).

And if you do still want to use Amarok instead (it's similar to Rhythmbox; has a few fancy features but is a bit heavier to run; I prefer Rhythmbox myself), it's as easy as:
```

sudo apt-get install amarok
```

---

### Post by ornovscot on 2008-07-29
Hi.

Thank you much for the reply.  I followed the steps for Rhythmbox, and I selected "New Internet Radio Station".

In the box that reads New Internet Radio Station, in the field for the URL I typed in the server ip address and the port number
(actually the server ip address and the port number of my station).

I received the message "Couldn't start playback".

It read "You do not have a decoder installed to handle this file.
You might need to install the necessary plugins."

The server address is [http://209.62.91.116:6000](http://209.62.91.116:6000)

I tried this both ways with the latter address and the latter address with /listen.pls.



Should I install Real Player?  I have the basic book about Ubuntu.

---

### Post by pytheas22 on 2008-07-29
> It read "You do not have a decoder installed to handle this file.
You might need to install the necessary plugins."

Try running the command:
```

sudo apt-get install ubuntu-restricted-extras
```

It will install all of the proprietary multimedia codecs and hopefully solve the problem.
> 
Should I install Real Player? I have the basic book about Ubuntu. 

I don't even know if you can install Real Player on Linux.  If you want a media player that comes with codecs already installed, try [VLC]("http://www.videolan.org/vlc/").  VLC comes with codecs built-in; it doesn't rely on system-wide libraries.

But again, once you run the command above, you should have all codecs available to all applications.

---

### Post by ornovscot on 2008-07-29
Thank you again.  I really appreciate your patience.

In the terminal window I typed in the command you recommended, and it read "Couldn't find package unbuntu-restricted-extras

---

### Post by pytheas22 on 2008-07-29
You must not have all of the repositories enabled (sorry for not thinking to mention it before).  Go to System>Administration>Software Sources.  Under the Ubuntu Software tab, make sure that all of the boxes are checked (the source code one is optional).  Then close the window.  You should be asked if you want to reload the repository list; say yes.  After it finishes downloading the new stuff, try running the sudo apt-get command again.  Does it work now?

---

### Post by ornovscot on 2008-07-29
After I did everything recommended and typed in the sudo-get install command, I received a long list of lines, at the end of which it asks whether I want to continue.

Do I answer yes by typing in Y

I'm sorry my questions are rather obvious.

Thank you kindly again.





P.S...   I indicated Y, and it seemed downloading took place.  Then I was presented with a message with a blue background, which read
msttcorefonts uses defoma

Msttcorefonts uses the DEbian FOnt MAnager (defoma).  If you wish.....

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required.

Then in red is an OK selection.

---

### Post by ornovscot on 2008-07-29
I'm sorry.  After making the changes above, after I select New Internet Radio Station and type in [http://209.62.91.116:6000](http://209.62.91.116:6000), 
I get the same error message above.

I might try to download realplayer for linux, as described in the book entitled "Ubuntus Linux for Non-Geeks".

As you can tell, I'm not terribly technical.

Thank you for all your patient and kind help.

Charlie

---

### Post by pytheas22 on 2008-07-29
Sorry it's still not working.  Would you mind giving me the URL that you're trying to play so that I can check to see if I have a problem with it?

You can try installing RealPlayer if you like--if your book recommends it than I'm sure it can be done--but RealPLayer is closed-source and can do some sketchy things, in my experience (like do stuff in the background and not ask you about it).  That may not bother you, but if you're like me, you're better off using open-source stuff and not have to worry about it doing creepy things.  I'm sure there's a way to get this working using open-source players; we just need to figure out what's wrong.

---

### Post by ornovscot on 2008-07-29
The listening link works in the different Windows computers I have here.  It doesn't work in the Ubuntu computer, even after making all the changes.  Additionally, after I made those changes even the radio station, Virgin radio, that was listed wouldn't play as it did before.

Here is the listening link for my station:


[http://209.62.91.116:6000/listen.pls](http://209.62.91.116:6000/listen.pls)


In the meantime, I did download the Real Player for linux; I followed all the steps.  And the test Real Player appears, that is, the image.  But when I click onto the real player icon on my station's website, nothing seems to happen.  I get a dialogue box, but the Real Player audio player doesn't launch.

I'm confused.  I hope I didn't make things worse.

Thank you again.

---

### Post by pytheas22 on 2008-07-29
hmmm, it plays fine for me in Rhythmbox and Movie Player.  Do you have better luck if you open up Movie Player (also under Applications>Sound and Video), select "Open Location" and put "http://209.62.91.116:6000/listen.pls" into the box?  If not, do you get an error message?

Also, is this the exact and full error message that you got from Rhythmbox:

> 
You do not have a decoder installed to handle this file.
You might need to install the necessary plugins.

I'll do some searching and see if I can find anything.

Also, if you have an mp3 on your computer, are you able to play that?

---

### Post by mick222 on 2008-07-29
that url gives an error in firefox . do you have the mplayer plugin installed . realplayer is not great in linux

---

### Post by ornovscot on 2008-07-29
The real player seems to work.

About the URL in Firefox, you're right.  When I typed into the address bar [http://209.62.91.116:6000/listen.pls](http://209.62.91.116:6000/listen.pls), I received the message to the effect that the address was restricted.  

Were you to use Windows Explorer perhaps this might not happen.  Even Firefox on my Windows computer doesn't open all of the audio players on my website.

For reference, my website is [www.radioorenovscotia.com](www.radioorenovscotia.com)


I'm sorry for the false alarm.


Thank you again.

Charlie

---

