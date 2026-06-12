---
title: "HOWTO:  Simple, complete audio and video setup"
date: 2010-05-15
forum: Multimedia Software
---

### Post by jacrider on 2010-05-15
After many years of using Ubuntu and other Linux os's, I have come to a standard set of audio and video applications that work well together.

My desire is for high quality audio and video.  While I am fairly technically adept, I look for effective applications that get the job done with the least complexity.

Audio:

1.  **Rhythmbox**.  I know other people will say Amarok or Songbird are better.  That could be.  Rhythmbox works.  The user interface is simple and intuitive.  I manages my music library easily and it plays nicely.  It plays all codecs.  It also allows you to transfer tracks to an iPod or other player.  That is just about everything I need in an audio player.  Further, it comes standard in Ubuntu.

2.  **Sound Juicer**.  Again, I know other apps are out there to rip CD's.  Sound Juicer just works.  It has a simple UI.  The output codec options are complete and you have enough control over parameters if you need.  I usually rip to .flac files, which it does nicely.  It sources the meta data properly from the Internet.  Simple and functional.

3.  **SoundConverter**.  A simple GUI application to take audio files and convert the codec.  As I rip most of my CD's into flac files, if I want to put them on to an iPod, SoundConverter does a nice job converting the flac files to either MP3 or aac files.  Fast, simple and intuitive.

4.  **gtkPod**.  A very simple tool to manage the content on an iPod that runs the Apple firmware (ie. not a unit that has been Rockboxed).  Again, simple intuitive tool to move files to and from an iPod.  Most of this can be done in Rhythmbox, but this is even more simple.

5.  **Rockbox**.  This is one I am just starting to play with, so more learnings to be had here.  I am using it to be able play higher quality flac files on my iPod.  Looks promising so far.  Linux on an iPod!  There doesn't appear to be a content management tool for Rockbox - just use Nautilus or Konqueror.  There appear to be lots of options to customize your Rockboxed player, but I am using the stock theme and options.  Not an issue for me, but no video support yet.  Rockbox doesn't replace the Apple firmware, so you are effectively dual booting - nice option.


Video:

1.  **VLC**.  A complete video player.  Just about all the codecs you could want are supported.  Simple UI, but if you are looking for lots of options and customization, it is available.  Not much else to say there.  Truth is I don't watch a lot of file-based video on my computer.  That is what a TV is for.  As such, VLC is perfect for the occasional need.

2.  **Handbrake**.  Quite simply the best DVD ripping tool anywhere.  Dead simple user interface.  Great codec support.  My family uses iPods for portable video and we have an AppleTV for viewing movies on a TV.  Using Handbrake, if you select the Apple Universal codec, you can create an output file that works anywhere - VLC, AppleTV, ipods, etc.  Fast, if you computer is.  Video ripping is heavy lifting for your CPU.


Equipment:

1.  Decent **soundcard**.  I am on a desktop and have added a great soundcard and it makes a huge difference over the onboard audio.  I have an Asus Xonar STX, but a good Soundblaster or other brand would also be a good upgrade.

2.  Decent **speakers**.  Again, as I don't really watch movies on my computer those small  surround speaker systems with a subwoofer aren't needed.  I have a good set of powered stereo speakers, so they will work with a computer, laptop, iPod, etc.  I have Audioengine A2's and like them, but there are others out there that are also much better than the standard $20 computer speakers.


Conclusion:  With this simple set of tools and equipment, I am easily able to enjoy great audio and video in Ubuntu.  Nothing is complicated or difficult to use.  All of the above applications are available in Ubuntu's Software Center except for Handbrake and Rockbox.  Handbrake's website has a .deb to download and install easily.  Everything works and in true open-source style, you have complete control over all of your content.

Thanks, hope this helps.

jacrider

---

### Post by JohnAStebbins on 2010-05-15
The 0.9.4 release deb on HandBrake's download page doesn't work on lucid.  You must use the snapshot releases that are available here [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by jacrider on 2010-05-15
Thanks for the info on Handbrake.  I'm still on 9.10, so I haven't faced that yet.

---

