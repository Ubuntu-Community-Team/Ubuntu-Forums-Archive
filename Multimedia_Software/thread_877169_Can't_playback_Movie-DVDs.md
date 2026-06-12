---
title: "Can't playback Movie-DVDs"
date: 2008-08-01
forum: Multimedia Software
---

### Post by airflow on 2008-08-01
Hi!

I have the problem that I can't playback DVDs on my system. When I try to do that, I get

```
Aug  1 19:44:26 AQUARIUS kernel: [ 3578.566964] end_request: I/O error, dev sr1, sector 607584
Aug  1 19:44:26 AQUARIUS kernel: [ 3578.709728] end_request: I/O error, dev sr1, sector 607584
Aug  1 19:44:26 AQUARIUS kernel: [ 3578.852539] end_request: I/O error, dev sr1, sector 607584
Aug  1 19:44:26 AQUARIUS kernel: [ 3578.995212] end_request: I/O error, dev sr1, sector 607584
Aug  1 19:44:26 AQUARIUS kernel: [ 3579.138003] end_request: I/O error, dev sr1, sector 607584
Aug  1 19:44:27 AQUARIUS kernel: [ 3579.280728] end_request: I/O error, dev sr1, sector 607584

```

Looks like faulty hardware, but the DVD is in perfect condition and can be normally played with other hardware. And the drive in my PC can also normally read DATA-DVDs. DATA-DVDs are no problem, but with Movie-DVDs I have always this problem - with every Movie-DVD I have tried so far!?

Anybody can give a hint what the problem could be?

Thanks,
airflow

---

### Post by airflow on 2008-08-01
I'd like to add that I just tried to playback the same DVD on the same computer with Windows XP (dual boot)! :( There must be something wrong with my ubuntu-configuration...

greez,
airflow

---

### Post by sstvinc2 on 2008-08-01
Have you already installed the extra gstreamer packages?  Applications -> Add/Remove, search all apps for gstreamer.  Install "gstreamer ffmpeg..." and "gstreamer extra plugins".

---

### Post by sstvinc2 on 2008-08-01
Or actually install the restricted formats stuff: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats").  My bad.

---

### Post by loboc on 2008-08-01
```
 sudo apt-get install libdvdcss2 
```


If its not there may I introduce you to medibuntu and the world of restricted packages.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by silkstone on 2008-08-01
First you must enable the Medibuntu repository...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then install the following in order to play DVDs...

```
sudo apt-get install libdvdcss2
```

There are many other codecs you can also install, but perhaps you already have. Ask if you need some help!

---

### Post by airflow on 2008-08-17
> **silkstone said:**
> First you must enable the Medibuntu repository...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then install the following in order to play DVDs...

```
sudo apt-get install libdvdcss2
```

There are many other codecs you can also install, but perhaps you already have. Ask if you need some help!

Thanks for your input, this helped.

regards,
airflow

---

