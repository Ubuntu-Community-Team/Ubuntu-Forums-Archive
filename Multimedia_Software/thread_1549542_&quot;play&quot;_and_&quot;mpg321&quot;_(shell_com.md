---
title: "&quot;play&quot; and &quot;mpg321&quot; (shell commands) not opening .pls file"
date: 2010-08-09
forum: Multimedia Software
---

### Post by EduardoMartins on 2010-08-09
Hi,

I tried playing a playlist file from a radio station with:

```
play http://www.heavymetalradio.com/listen.pls
```But got the error:

```
user@system76-pc:~$ play http://www.heavymetalradio.com/listen.pls
play FAIL formats: no handler for file extension `215:8024'
```Then I tried:

```
mpg321 http://www.heavymetalradio.com/listen.pls
```But got the following message (and nothing happened):

```
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

Directory: http:/
Playing MPEG stream from www.heavymetalradio.com ...

[0:00] Decoding of www.heavymetalradio.com finished.
```How can I properly play .pls files with a shell program (no GUI)?

Thanks,

Eduardo

---

### Post by andrew.46 on 2010-08-12
Hi eduardo,

Try:

```

mplayer -playlist http://www.heavymetalradio.com/listen.pls

```

Andrew

---

### Post by mc4man on 2010-08-13
for mpg321 several ways
```
mpg123 -@http://www.heavymetalradio.com/listen.pls
```

```
mpg123 http://www.heavymetalradio.com:8000
```

```
mpg123 http://87.98.172.215:8024
```

---

### Post by EduardoMartins on 2010-08-13
Thanks to you all!

@andrew.46 &#8594; it worked!

@mc4man &#8594; got the following errors:

```
user@system76-pc:~$ mpg123 -@http://www.heavymetalradio.com/listen.pls
http://www.heavymetalradio.com/listen.pls: No such file or directory
``````
user@system76-pc:~$ mpg123 http://www.heavymetalradio.com:8000
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
http://www.heavymetalradio.com:8000: No such file or directory
``````
user@system76-pc:~$ mpg123 http://87.98.172.215:8024
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
http://87.98.172.215:8024: No such file or directory
```Anyway, the only thing left to make it perfect is being able to run in the background, liberating the shell for other purposes. How can it be done?

Eduardo

---

### Post by andrew.46 on 2010-08-13
Hi Eduardo,

You seem to have quite an old version of mpg123 there, I am not sure if this might be part of the problem:

```

andrew@skamandros~$ **[COLOR="Red"]mpg123 http://www.heavymetalradio.com:8000[/COLOR]**
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	**[COLOR="Red"]version 1.12.3[/COLOR]**; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes

Directory: http://
Playing MPEG stream 1 of 1: www.heavymetalradio.com:8000 ...
ICY-NAME: HeavyMetalRadio.com - The Loudest Site on the Internet!!!  - Request from over 65K Songs  on Website!
ICY-URL: http://www.heavymetalradio.com
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz stereo

ICY-META: StreamTitle='Crimson Glory - Azrael';StreamUrl='&artist=Crimson%20Glory&title=Azrael&album=Crimson%20Glory&duration=337591&songtype=S&overlay=no&buycd=http%3A%2F%2Fwww%2Eamazon%2Ecom%2Fexec%2Fobidos%2Fredirect%3Ftag%3Dheavymetalrad%2D20%2526creativ';


```

I am not on my Ubuntu partition at the moment so I am not completely sure what is available from the repository. Seems like mpg321 is also having a revival at the momen just to confuse things more than a little :).

Andrew

---

