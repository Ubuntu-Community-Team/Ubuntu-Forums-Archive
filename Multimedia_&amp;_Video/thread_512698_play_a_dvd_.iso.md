---
title: "play a dvd .iso"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by Chymera on 2007-07-29
I have a dvd on my hard drive. i have tried playing it with numerous players and couldnt get it to work with either of them.

1)Kaffeine
I click open directory in the file menu, select the directory. and get the following error message " xine: couldn't find demux for: <name of the movie>"

2)VLC media player
Gets the file playing but dosnt render any video stream, or sometimes just a bit of video at the begining.

3)MPlayer
I get "Error opening/initializing the selecthed video_out (-vo) device."

4)Totem (xine) 
gives me "There is no plugin to handle this file"

any sugestions?

---

### Post by dan_m on 2007-07-29
I'm sorry if I misunderstood your problem!

If it's what I understood, you tried to play a DVD with a .iso file.
You can't.
This is an image of an actual DVD.
[http://www.answers.com/topic/iso-image](http://www.answers.com/topic/iso-image)

In order to play it, you have to burn it on a blank DVD.
Use:
Aplications / Sound & Video / CD/DVD Writer GnomeBaker
Tools / Write DVD image.
BTW, in Windows XP, Total Commander, there is a plugin which lets you see the content of an .iso file as in a folder.

If you are more experienced and this was not the problem, pls forgive me.

---

### Post by Lord Illidan on 2007-07-29
Vlc should be able to read .isos...
I have Underworld 1 as a dvd .iso and it plays over there..

Can you try burning the iso?

---

### Post by Chymera on 2007-07-29
to dan_m: no problem, under linux you have a series of players which at least claim to be able to play dvds directly from an .iso file.

to ilidan: i mounted the iso, and was able to play it with kaffeine. Sice you say you have vlc could you tell me why, even with the iso mounted, it only plays the sound? actually, it continues to play the sound even after i have closed the window, so i usually have to shut it down from system monitor...

---

### Post by Vincent_Lin on 2007-07-29
VLC out of the box should be able to play iso image of a DVD movie.  My mythtv setup uses VLC to play DVD images as iso, perfectly.  The problem that you can't play iso image of a DVD movie even using VLC indicates to me that this iso file is at fault.  Someone mentioned that to check if you can burn into a DVD movie by this iso image is a pretty good way to check it.

Sometimes when your x is running composite manager, such as beryl or something, you should check if the video coding/encoding methods in VLC which might interfere your normal playing.  Try to use VLC to play a physical DVD movie to check if your VLC's setting is correct for your X setup.  make sure you can play a physical DVD movie perfectly (to make sure video/audio setting of VLC is correct in terms of you X setting) before you try to play an iso image of DVD movie.

Cheers,

Vincent

---

### Post by Chymera on 2007-07-30
Since i said in my previous post that i was able to play the dvd with kaffeine, once i mounted it, it most obviously wasnt broken. As for vcl, i tried to play a real dvd with it, one that could be played by kaffeine too, and i get the same problem: sound ok, but no video stream. Do you have any idea what settings would work with beryl?

---

### Post by adzik on 2007-09-14
I used to be able to playback ISO files directly under Totem in Edgy. It doesn't work in feisty. Has anyone else experienced this? Just curious.... for now I just mount my images.

---

### Post by Chymera on 2007-09-14
yes, I have experienced it about a month ago, and am experiencing it ever since.... interesting experience what can i say :confused:

---

### Post by livia on 2007-09-18
You can play ISOs directly with VLC or Kaffeine. You can play it with mplayer or xine if you specify the path to your ISO image in _command line_:

xine dvd:/path/to/your/DVD/image.iso
mplayer dvd://1 -dvd-device /path/to/your/DVD/image.iso

The latter example will play DVD title #1. It's even easier with mplayer:

mplayer DVD.iso

But mplayer isn't good for watching DVDs yet. It has some support for DVD menus via libdvdnav, but it's still buggy now.

VLC and kaffeine support playing DVDs from folder. You'll find that option in their menu. Xine can do this, too, but via command line, exactly in the same way as it does with ISOs, just specify the path to VIDEO_TS:

xine dvd://path/to/your/DVD/VIDEO_TS/

---

### Post by mommebu on 2007-11-21
While in earlier versions of ubuntu totem-xine was able to play iso files it seems to fail now if you load the image from the menu, however from terminal it worked for me using:
totem-xine dvd://absolute/path/to/your/iso/file.iso &
This is without mounting the image.

Strange that the newer version lost the feature from the menu though...

---

### Post by quadCoreBrainWithNoMemory on 2008-05-17
I wanted konqueror to handle iso files with Kaffeine.  I created a small perl script called kaffiene-iso-wrapper.pl and set it as the default application for iso images.
[B][FONT="Courier New"]
> cd ~/bin/
> kate kaffiene-iso-wrapper.pl[/FONT][/B]
I added the following to the file
```
#!/usr/bin/perl

foreach my $arg (@ARGV)
{
	if ($arg =~ /\.iso$/)
	{
		if ($arg =~ m#^~/#)
		{
			$arg =~ s#^~/#$ENV{'HOME'}/#;
		}
		elsif ($arg !~ m#^/#)
		{
			$arg = $ENV{'PWD'}/$arg;
		}

		$arg =~ s#^#dvd://#;
	}
}

print "kaffeine @ARGV\n";
system "kaffeine", @ARGV;

```

I also changed the settings so it was an executable script:
[B][FONT="Courier New"]
> chmod u+x kaffiene-iso-wrapper.pl[/FONT][/B]
Then I started kcontrol, and performed a search for filetypes, selected *file associations*, searched for "iso", and chose **x-iso**, and you can see the rest in this picture:
[IMG]http://farm4.static.flickr.com/3156/2499141922_4209085a73_o.jpg[/IMG]

---

