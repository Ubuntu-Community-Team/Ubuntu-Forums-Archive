---
title: "flv Transcoding to PS3"
date: 2008-04-07
forum: Multimedia Production
---

### Post by Svalde on 2008-04-07
Hi,

I have tried to transcode a .flv file to my PS3 with mediatomb. I have found a guide om mediatomb.cc, but I can't get it to work, I tried to posting a thread i the mediatomb forum, and some guy there told me that it most likely was some permission problems.

here is the post with some details: [http://sourceforge.net/forum/forum.php?thread_id=1995857&forum_id=440751]("http://sourceforge.net/forum/forum.php?thread_id=1995857&forum_id=440751")

Thanks in advance, Anders.

---

### Post by tamoneya on 2008-04-07
it does seem to be a permissions problem to me.  Lets see if it works if you call using sudo.  Take whatever command you used to start it and place "sudo " before it.

---

### Post by Svalde on 2008-04-08
Hi,

I tried adding sudo to my code, but I just got a new error.

2008-04-08 21:16:56   ERROR: error in configuration, transcoding profile "vlcmpeg" could not find transcoding command sudo vlc in $PATH

This is the line in witch I call the VLC player: <agent **command="vlc"** arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>

I believe that the bold selection is where I tell the program to use VLC, but when I add SUDO I get the new error.

/Anders

---

### Post by Svalde on 2008-04-09
Hi again,

I figured it out. :)

When i ran mediatomb I used the commend "sudo mediatomb", so instead of adding "sudo" to my script I tried running mediatomb without the sudo command.

Thanks for the help. :)

/Anders.

---

