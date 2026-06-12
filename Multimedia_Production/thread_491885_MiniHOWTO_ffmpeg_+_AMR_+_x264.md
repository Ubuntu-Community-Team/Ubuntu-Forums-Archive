---
title: "MiniHOWTO: ffmpeg + AMR + x264"
date: 2007-07-04
forum: Multimedia Production
---

### Post by martin_lindhe on 2007-07-04
Here's a quick walkthru on how to install ffmpeg properly with AMR + x264 (for dealing with 3GPP audio & video). The following steps should be enough if you start with a fresh Ubuntu 7.04 install.

1. Install required components

```
sudo apt-get install g++ subversion nasm zlib1g-dev libx264-dev
```

2. Install AMR

The latest versions of AMR can be found here: [http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

AMR-NB
```

wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-6.1.0.4.tar.bz2
tar -jxvf amrnb-6.1.0.4.tar.bz2
cd amrnb-6.1.0.4

./configure --prefix=/usr
make
sudo make install

```


AMR-WB
```

wget http://ftp.penguin.cz/pub/users/utx/amr/amrwb-7.0.0.1.tar.bz2
tar -jxvf amrwb-7.0.0.1.tar.bz2
cd amrwb-7.0.0.1

./configure --prefix=/usr
make
sudo make install

```

3. Get the latest ffmpeg source
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg-svn
```

4. Compile ffmpeg

```

cd ffmpeg-svn

./configure --enable-gpl --enable-pthreads --enable-libx264 --enable-libamr-nb --enable-libamr-wb
make

```

---

### Post by psavva on 2008-02-01
Thank You... Very useful Howto :D

---

### Post by bcmoney on 2008-02-25
Excellent article... thx

---

### Post by tdtran on 2008-04-08
Thanks for the article.
I am a newbie.

I have tried to install the encoder and ffmpeg, but when i converted an MP3 to amr as

ffmpeg -i in.mp3 -acodec amrnb -ar 8000 -ac 1 -ab 32 out.amr

I got the error:

Unknown encoder 'amrnb'

When i enter "amrnb-encoder" at the console i got the message printed out as:

Usage of amrnb-encoder:

[-dtx] mode speech_file bitstream_file 

.......

Does that mean amrnb has been installed ?
But if so, then why the ffmpeg does not recognize the encoder as i have specified ?

Please help me out of this.

---

### Post by idhaya on 2008-07-10
Hi Did u get the solution for ur ques?
am trying to encode to amr-nb but it throws the error as unsupported codec

---

### Post by dearephesus64 on 2008-07-12
Still not a lot of luck

While following this howto on Hardy, it told me that libamr was non free and "--enable-nonfree" was not specified.  Genius that I am, it took me a while to realize that it wanted me to specify "--enable-nonfree" so that it could use the non-free libraries.  Duh.

So, if the second to last step gives you an error message, instead of the code from above,

USE THIS IN THE SECOND TO LAST STEP:

```
./configure --enable-nonfree --enable-gpl --enable-pthreads --enable-libx264 --enable-libamr-nb --enable-libamr-wb
make

```

I just added --enable-nonfree to the front.

Still didn't quite make it though-there was an "error 1" and something about X264_ME_TESA being undeclared.  Another couple steps. 

*(I just want to use 3gpconverter to make videos to put on my phone; it shouldn't be this hard!  I can't complain though because I'm kinda having fun with this.)*

I had to search the forum and I came up with an answer on page 3 of this thread:

[http://ubuntuforums.org/showthread.php?t=693867&highlight=X264_ME_TESA+undeclared]("http://ubuntuforums.org/showthread.php?t=693867&highlight=X264_ME_TESA+undeclared")

(thanks, "anal" for the useful post.  I don't understand what I'm doing either though :) )

So I installed those packages and then it compiled for me.

But it still doesn't show up in 3gpconverter as having support for the amr audio, and 3gp videos I already have still don't have sound.  

I give up.

---

