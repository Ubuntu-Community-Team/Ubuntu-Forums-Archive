---
title: "There has to be an easier way... iPod on Ubuntu"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by sharong on 2007-06-25
I have an iPod shuffle and a Nano, and I've finally got them working, but I'm convinced there has to be an easier way.  Here's what I have to do to get a CD onto them:

Rip CD using Sound Juicer - this gives me an Ogg Vorbis File.

Convert Ogg Vorbis file to wav using Sound Convertor (which gives me the option of mp3, but I can't enable it).

Convert wav files to mp3 using lame.

Add mp3 tags using AudioTag.

Copy to iPod using gtkpod.

Is there an easier way of doing this?

Additionally, when I connect to iTunes, it can't read the database, and it then wipes everything (both the iPods were both used first on Ubuntu; although the shuffle is 2nd hand refurbished so I don't know how it was used before).  This is really annoying, because effectively it means I can't use iTunes and therefore can't download any music - unless I want to wipe everything that's already on the iPod.  So the only way to get stuff onto my iPod is to rip a CD or download in mp3 format in the first place (but there's not much available that way).

So, can anyone suggest a more efficient way of doing things?

Thanks!!

---

### Post by frodon on 2007-06-25
Grip allows you to rip your song and convert it directly in the MP3 format in a single operation.

Now for the database and sync matters it's the drawback of full proprietary architecture almost all other players don't need that so you can just drop your files on the player, the solution :
Don't buy Ipods !

---

### Post by kellsens on 2007-06-25
Hi Sharong,

  Like Frodon said, Grip can rip, convert and tag your cd songs to mp3. To manager your Ipod, without problems, try use [Yamipod]("http://www.yamipod.com/") . I have an Ipod 30Gb and use it.

Kellsens

P.S.: Sorry my english

---

### Post by onero on 2007-06-25
I use amarok for my ipod since it automatically detects such devices. I know there are other media players that support ipods as well; try it if it works for you.

---

### Post by sharong on 2007-06-25
Thanks for the responses - I tried gRip, but it didn't work - I think it did everything, extracted and converted etc, but then deleted everything it had produced - it was something really stupid like that.  I'll try it again though.

I know iPods are really awkward, but I won it in a competition, so I didn't have any choice!!!

---

### Post by rfurman24 on 2007-06-25
I use grip or kaudiocreator, both work great. I use GTKpod and have no problem with Itunes, but I quit using windows altogether after getting gtkpod going. It was my last need for windows.

---

### Post by Darin on 2007-07-19
One thing you need to do to rip straight to MP3 from Sound Juicer is to install the gstreamer ugly plugins. Just do a search for "gstreamer ugly" in Synaptic. Be sure to install both gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse.

If these don't show up when you first search, you need to go to Settings->Repositories and enable the Multiverse (and Universe while you're at it) repositories. Then just reload and search again.

After you've installed the gstreamer plugins, just go to the Preferences in Sound Juicer and select the MP3 format. The default is a Variable Bitrate format. You can add Constant Bitrate by adding a new profile and adding this for the pipeline:
```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192 ! id3v2mux
```
Changing the bitrate from 192 to whatever you want.

Note: If you're using Ubuntu Feisty 7.04, there is a bug when adding a audio profile. When you try to edit an audio profile, it won't let you edit the top window. Just move the "Editing Profile" window out of the way, and close the window titled "Edit GNOME Audio Profiles".

Anyway, once you install the ugly plugins, it should be much easier.

Sound Juicer can rip your CDs to mp3, and also tag them automatically. If not automatically, you can do it manually through Sound Juicer before they are ripped. You shouldn't have to rip first, the tag with something else later.

Have you tried the Rhythmbox Music Player? It can rip, do basic tagging, and manage your iPod, and PC Library. Should be very simple. It also uses the same sound profiles as Sound Juicer, so once you set up Sound Juicer, Rhythmbox should already be set up.

Other players can do the same, such as Amarok. Banshee and I believe also Exaile should also be able to do the same. Though these players may use different methods and need to be set up for MP3 ripping, I'm not sure. Maybe someone else can comment.

Anyway, hope this helps. I find Rhythmbox very nice for ripping, and managing music. It should be able to do everything you want. But if you don't want to use it, all you should need is Sound Juicer and GTKPod (or Yamipod or any other iPod manager). You shouldn't need anymore than one ripper and one iPod manager to do all you want.

As for the iTunes situation, I'm sorry I don't know much about that and can't help. Maybe someone else can chime in. But hope the rest of this helps!

- Darin

---

### Post by bharris25 on 2007-11-10
I don't think there is a way around ITunes wiping your music because that is what Apple wants, they want you to sync your Ipod with only one ITunes on one computer, any time you try to sync your Ipod with another computer's ITunes it will make you wipe the Ipod.  As for music you buy from ITunes store you should back that stuff up with Amorok or some other media player on your linux system, I use amorok and it is pretty good, plug your Ipod in and it sees it and it pops a window up wanting to know I you want amorok to manage it and it has a button to say it's an ipod and then you can access it.  But I agree with the not buying Ipod, I will not buy another one because you cannot use the next generation of Ipods easily with linux because you have to use ITunes now.  It would cost apple nothing to include support for ogg files and to support open source just to stick it to Microsoft.

---

