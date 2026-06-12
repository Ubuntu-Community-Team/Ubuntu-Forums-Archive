---
title: "Forwarding audio over the network"
date: 2015-06-04
forum: Multimedia Software
---

### Post by ecooper7 on 2015-06-04
Hi all,

My typical workflow is to use my macbook running Mac OS X to log into one of many remote servers running Ubuntu.  I work with audio a lot, mainly .wav files, and to be able to listen to them, I generally have to scp them from the server where they live, over to my laptop.  It seems like there ought to be a better way to do this.

My ideal solution would be one where, from my ssh session on my laptop, I could just say "play foo.wav" and I would hear the audio come out of my laptop speakers.  I've been searching around about how to do this, and everyone seems to recommend using PulseAudio, but it's not really supported on Mac OS X as far as I can tell.

I was able to send the data of an individual .wav file over netcat and listen for it on my laptop, but that doesn't seem like a really general solution.  Ideally I would have a port open where I listen for *any* audio that happens on the remote server.

My servers are running a range of Ubuntu versions, from around 10.04 up to 14.04, and to complicate matters, many of them are headless and don't actually have a sound card.

Is there any way to set up PulseAudio on my servers to capture any system audio and send it to a TCP port, and then connect and listen for it on my laptop?

I apologize if this isn't quite the right place for this question, I realize it's not strictly an Ubuntu question as there is Mac OS X involved as well, but any advice or pointers would be greatly appreciated.

---

### Post by tgalati4 on 2015-06-04
You could dump the files to *mediatomb* on your server and then play/stream them through a web interface.  There are several web-based media servers, just pick one and set up your directories using remote mounts and when you dump files on your server they will show up in the web interface.  Another method involves running a DAAP music share and using iTunes to play the music share.

---

### Post by Bucky Ball on 2015-06-04
Welcome. I use Gigolo. Mounts remote partitions on the desktop like a local one. Simply click your audio files and play as if they were on the local machine. 

Gigolo can be found in the repositories (Software Centre or Synaptics) or by installing via a terminal. You can set them up the same way manually (and add to fstab so mounts at boot), and I did it that way years ago, but I discovered Gigolo just recently and decided to try that. Works for me.

---

