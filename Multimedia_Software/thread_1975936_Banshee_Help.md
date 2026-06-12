---
title: "Banshee Help"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Shadius on 2012-05-08
Hi all, 

I need some help with Banshee. I've tried using the Help in Banshee, but couldn't find my answer there so here I am. My issue is that I want to change the filename of my music files to match the metadata of the MP3.
 
For example, say I have a an MP3 file named *Artist - Title.mp3* and I change the metadata of the Artist and the Title, I assumed once I saved my changes that I made to the tag, that the filename would be renamed with that information, but that didn't happen.

Am I doing something wrong? Please help. I like to keep my music organized because I have a ton! I came from using MediaMonkey in Windows, if that helps you to understand what I'm looking for.

---

### Post by fballem on 2012-05-08
May I suggest a different approach? I use Banshee for playing my music and for synching to my mobile music devices. I have installed and use a program called EasyTag from the repositories to manage the meta data for the music files. The program does take a little bit to learn, but the documentation is quite good and it does a very nice job with my library. For example, I like my files to be named %d-%n-%t.flac (disc-track number-title) within the Artist-Album hierarchy. This is very easy to do.

---

### Post by Shadius on 2012-05-08
> **fballem said:**
> May I suggest a different approach? I use Banshee for playing my music and for synching to my mobile music devices. I have installed and use a program called EasyTag from the repositories to manage the meta data for the music files. The program does take a little bit to learn, but the documentation is quite good and it does a very nice job with my library. For example, I like my files to be named %d-%n-%t.flac (disc-track number-title) within the Artist-Album hierarchy. This is very easy to do.

Thank you for offering that approach. So I'm guessing Banshee doesn't allow you to do what EasyTag does? Is EasyTag a plugin for Banshee or another program?

---

### Post by fballem on 2012-05-08
EasyTag is a different program, which is primarily designed to manage labels on media files - which is exactly what you want to do. After you have used the program, and gotten the files exactly the way you want it, then you will have to rescan your library into Banshee.

Easytag can be installed using the Ubuntu Software Center. If you are comfortable using a Terminal, then the following command will install Easytag:
```

sudo apt-get install easytag
```

Once it is installed, it can be started from the Dashboard.

Enjoy,

---

### Post by Shadius on 2012-05-08
> **fballem said:**
> EasyTag is a different program, which is primarily designed to manage labels on media files - which is exactly what you want to do. After you have used the program, and gotten the files exactly the way you want it, then you will have to rescan your library into Banshee.

Easytag can be installed using the Ubuntu Software Center. If you are comfortable using a Terminal, then the following command will install Easytag:
```

sudo apt-get install easytag
```

Once it is installed, it can be started from the Dashboard.

Enjoy,

Thank you for providing both methods of installation! I used the Terminal method. Everything went well. Going to start to use the program now. If I run into any  problems, I'll report back here. Thanks again!

---

