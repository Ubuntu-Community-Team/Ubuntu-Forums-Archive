---
title: "Bluray playback"
date: 2014-08-08
forum: Multimedia Software
---

### Post by mcse2000ca on 2014-08-08
Has anyone had any success getting this working directly from the disc without ripping it from the disc with MakeMKV?

---

### Post by mcse2000ca on 2014-08-09
I take it that's a no?

---

### Post by dylan87 on 2014-08-11
no, I hadn't any success neither but also would be interested if someone has a solution!?

---

### Post by mc4man on 2014-08-11
You could read thru here, may work, may not. I gave my laptop with bluray drive to my son so have no means to try..
[https://wiki.archlinux.org/index.php/BluRay](https://wiki.archlinux.org/index.php/BluRay)

---

### Post by shantiq on 2014-08-12
[[IMG]http://s20.postimg.org/56prw5wk9/bluray_VLC.jpg[/IMG]]("http://postimg.org/image/56prw5wk9/") yes mcse i have absolutely fine with VLC also can be "processed" with handbrake  ;  but it plays as is from this samsung external drive TSSTcorpBDDVDW SE-506BB TS00
; altho personally i prefer to go through handbrake to a 1080p mkv as i do not see any joy in anything whirring ::]]


**For VLC   you need   [**take 3 minutes to set up if all ok[B]]
[/B]
```
[COLOR=#000000][FONT=monospace]sudo apt-get install libaacs0 libbluray1 libbluray-bdj [/FONT][/COLOR]

```

[COLOR=#000000]then you need to [FONT=helvetica]**Fetch AACS keys**
[/FONT]
[/COLOR]```
[COLOR=#000000][FONT=monospace]mkdir ~/.config/aacs [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]curl http://vlc-aacs.whoknowsmy.name/files/KEYDB.cfg > ~/.config/aacs/KEYDB.cfg [/FONT][/COLOR]
```
[COLOR=#000000]
it looks like this in the file

[/COLOR]```
; processing keys| PK | 0x09F911029D74E35BD84156C5635688C0 ; v1
| PK | 0x455FE10422CA29C4933F95052B792AB2 ; v3
| PK | 0xF190A1E8178D80643494394F8031D9C8 ; v4
| PK | 0x7A5F8A09F833F7221BD41FA64C9C7933 ; v6-8
| PK | 0xC87294CE84F9CCEB5984B547EEC18D66 ; v9
| PK | 0x452F6E403CDF10714E41DFAA257D313F ; v10
| PK | 0x973940bb180e83266231ee596cef65b2 ; v3-4/7-10/12-13
| PK | 0x58ebdadf88dcc93304cbbedb9ee095f6 ; v14/15/16
| PK | 0x465fa8be828509014d05d2fcceff35d2 ; v17
| PK | 0xad5e546c46d72dc083aeb5686924e1b3 ; v18/19
| PK | 0x53fce78ecd352da50d526b5ee3d3d96b ; v20/21
| PK | 0xc32238976ff44a51e2d33553cfe85772 ; v23/25


; host certificate from PS3, v25
| HC | HOST_PRIV_KEY 0x668c9a75eefc8da4261938e271285061bb09f0dd \
     | HOST_CERT 0x0201005cffff80000039000065eac9878b85eff4 \
                 0xd77a62b1d600024ace68dd3366880e4f844f34b7 \
                 0x7a050135a20e73b626daea5157b32eb84bc6e87b \
                 0x0dee4d833ceada86120151002c3c66d5256f71cf \
                 0xa68b7e55ba1b351f3403434e \
     | HOST_NONCE 0x2923BE84E16CD6AE529049F1F1BBE9EBB3A6DB3C \
     | HOST_KEY_POINT 0x8A60C80BD60C23605FBE90B27BF96B2DB38195C1 \
                      0x801F54EB29E0F6EC57AC2B9168E88B2D56977508


; host certificate from unknown, v20
| HC | HOST_PRIV_KEY 0x567A6A8EFFFD8967651CF1BB8D15EDB6D2463555 \
     | HOST_CERT 0x0200005CFFFF0000006400006440BE797538E4FC \
                 0x369FC50BBE9F95CC694338210CDFACE0D2C878BA \
                 0xB96BB72BA5A29D0F7D2E9B836B4CE06781D93354 \
                 0x4E6258F1F38668B4733F24638CCB6F5B71220A22 \
                 0x20217367F833635E97784D9E \
     | HOST_NONCE 0x2923BE84E16CD6AE529049F1F1BBE9EBB3A6DB3C \
     | HOST_KEY_POINT 0x8A60C80BD60C23605FBE90B27BF96B2DB38195C1 \
                      0x801F54EB29E0F6EC57AC2B9168E88B2D56977508


; host certificate from aacskeys-0.4.0c original, v18
| HC | HOST_PRIV_KEY 0x8C8647FE2A70EF0388EA9E43F432CC441C6B108C \
     | HOST_CERT 0x0200005CFFFF000000AE00004142A5411F1E63F1 \
                 0x85581C876B939FB40B523BF69C004CA69E047606 \
                 0xEE5183C0ABEF1E7D04CB6E65260677E7B0573D08 \
                 0xE60957935503ED78F7E27B190B4A7CAFCBAFF4A2 \
                 0x836453ECF72E49668DAF1DB9 \
     | HOST_NONCE 0x2923BE84E16CD6AE529049F1F1BBE9EBB3A6DB3C \
     | HOST_KEY_POINT 0x8A60C80BD60C23605FBE90B27BF96B2DB38195C1 \
                      0x801F54EB29E0F6EC57AC2B9168E88B2D56977508


; host certificate from powerdvd 7, v12
| HC | HOST_PRIV_KEY 0x4737676058D7029452514F0AB186DC4CCA8C578F \
     | HOST_CERT 0x0200005cffff0000000c00006e3deb679b9a16ad \
                 0xfaa8e30878767ba6eb2a9b415385ad1181b4446c \
                 0x31e9a5dd2ab808b364ff15885bac490964318c9b \
                 0xf8029fcf76f688a54fbda03f6d9332ef04e5a613 \
                 0x12da85880a4d9cbb79d8602e \
     | HOST_NONCE 0x2923BE84E16CD6AE529049F1F1BBE9EBB3A6DB3C \
     | HOST_KEY_POINT 0x8A60C80BD60C23605FBE90B27BF96B2DB38195C1 \

                      0x801F54EB29E0F6EC57AC2B9168E88B2D56977508
```[COLOR=#000000]


[/COLOR]


guide[ here]("http://www.libregeek.org/2014/01/05/a-guide-to-playing-blu-rays-on-ubuntu-linux/")
guide 2 [here]("http://hydra.geht.net/tino/howto/linux/ubuntu/bluray/")

[IMG]http://images.samsung.com/is/image/samsung/sg_SE-506AB-TSBD_003_Dynamic?$Download-Source$[/IMG]

---

### Post by mcse2000ca on 2014-08-12
How old is the newest Blue-ray you have tried though?

---

### Post by shantiq on 2014-08-13
tried   2011     and fine   but also tried a 2013   disc   and no go   in any of the players won't even open in Handbrake to convert or be read by mediainfo/ffmpeg    ** the AAC keys do not reach to 2013**

[[IMG]http://s20.postimg.org/jv59kzme1/other.png[/IMG]]("http://postimg.org/image/jv59kzme1/")   **  vlc**


[[IMG]http://s20.postimg.org/o1limkwm1/other2.png[/IMG]]("http://postimg.org/image/o1limkwm1/")  **vlc specs**


[[IMG]http://s20.postimg.org/8u5j284rd/theotherguysbluraycoverart.jpg[/IMG]]("http://postimg.org/image/8u5j284rd/")     **2011**


[[IMG]http://s20.postimg.org/qzn2u0tnd/xbmc.png[/IMG]]("http://postimg.org/image/qzn2u0tnd/")**  xbmc**


also works with [mpv]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")    with this line    

```
mpv bd:// --bluray-device=/path/to/bd/

```

so   ```
mpv bd:// --bluray-device=/dev/sr0
```  or   ```
mpv bd:// --bluray-device=/dev/sr1
```


But the very best playback is[ XBMC]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_for_Linux")   really smooth and no stutter  [which i have on mine with VLC and MPV as my machine is 10 years old with a new graphics card   but will not be an issue on newer machines]




So try XBMC with the latest bluray you av see how you fare


PS   as regards bluray made in  the last 2 years  [ the Keys ]("http://vlc-bluray.whoknowsmy.name/")do not cut it are simply not up to date unless anyone knows better   .... i also tried on a Mac and same story
if you check the keys in [COLOR=#000000][FONT=monospace]KEYDB.cfg you will see they go to

[/FONT][/COLOR]| PK | 0xc32238976ff44a51e2d33553cfe85772 ; **v23/25**


and on the 2013 disc   they use**  protection v34 ,  QED , **if there are not more recent keys we cannot play blurays we have bought on our computers;   only in bluray players linked to a tv is what i understand but discs up to 2011 are ok it seems up to **v23/25**

---

### Post by ibhollow1975 on 2014-09-18
I have not been able to play the Big Lebowski on my computer and it uses AACS v23. So, do they keys really go up that high or am I doing something wrong? 

> **shantiq said:**
> tried   2011     and fine   but also tried a 2013   disc   and no go   in any of the players won't even open in Handbrake to convert or be read by mediainfo/ffmpeg    ** the AAC keys do not reach to 2013**

[[IMG]http://s20.postimg.org/jv59kzme1/other.png[/IMG]]("http://postimg.org/image/jv59kzme1/")   **  vlc**


[[IMG]http://s20.postimg.org/o1limkwm1/other2.png[/IMG]]("http://postimg.org/image/o1limkwm1/")  **vlc specs**


[[IMG]http://s20.postimg.org/8u5j284rd/theotherguysbluraycoverart.jpg[/IMG]]("http://postimg.org/image/8u5j284rd/")     **2011**


[[IMG]http://s20.postimg.org/qzn2u0tnd/xbmc.png[/IMG]]("http://postimg.org/image/qzn2u0tnd/")**  xbmc**


also works with [mpv]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")    with this line    

```
mpv bd:// --bluray-device=/path/to/bd/

```

so   ```
mpv bd:// --bluray-device=/dev/sr0
```  or   ```
mpv bd:// --bluray-device=/dev/sr1
```


But the very best playback is[ XBMC]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_for_Linux")   really smooth and no stutter  [which i have on mine with VLC and MPV as my machine is 10 years old with a new graphics card   but will not be an issue on newer machines]




So try XBMC with the latest bluray you av see how you fare


PS   as regards bluray made in  the last 2 years  [ the Keys ]("http://vlc-bluray.whoknowsmy.name/")do not cut it are simply not up to date unless anyone knows better   .... i also tried on a Mac and same story
if you check the keys in [COLOR=#000000][FONT=monospace]KEYDB.cfg you will see they go to

[/FONT][/COLOR]| PK | 0xc32238976ff44a51e2d33553cfe85772 ; **v23/25**


and on the 2013 disc   they use**  protection v34 ,  QED , **if there are not more recent keys we cannot play blurays we have bought on our computers;   only in bluray players linked to a tv is what i understand but discs up to 2011 are ok it seems up to **v23/25**

---

### Post by shantiq on 2014-09-18
have you tried

```
[COLOR=#000000][COLOR=#000000][FONT=monospace]sudo apt-get install libaacs0 libbluray1 libbluray-bdj [/FONT][/COLOR][/COLOR]

```[COLOR=#000000][COLOR=#000000]then you need to [FONT=helvetica]**Fetch AACS keys**
[/FONT][/COLOR][/COLOR][COLOR=#000000]
```
[COLOR=#000000][FONT=monospace]mkdir ~/.config/aacs [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]curl [http://vlc-aacs.whoknowsmy.name/files/KEYDB.cfg](http://vlc-aacs.whoknowsmy.name/files/KEYDB.cfg) > ~/.config/aacs/KEYDB.cfg [/FONT][/COLOR]
```


[/COLOR]
then install [xbmc]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_for_Linux")   and open your    Lebowski bluray   and The Dude should appear :)    best of luck

---

### Post by ibhollow1975 on 2014-09-18
OK I did all of that but XBMC does not even see my bluray drive. So how do you play it? 

I also have MakeMKV and it can decrypt the video. It will stream but when I go to play the stream on vlc all that plays is a bluray intro loop with scenes from the movie. Can anyone offer a solution on the MKV side? Their website says they can play ALL blurays because they have the most up to date AACS keys. Does anyone know anything about this? 

> **shantiq said:**
> have you tried

```
[COLOR=#000000][COLOR=#000000][FONT=monospace]sudo apt-get install libaacs0 libbluray1 libbluray-bdj [/FONT][/COLOR][/COLOR]

```[COLOR=#000000][COLOR=#000000]then you need to [FONT=helvetica]**Fetch AACS keys**
[/FONT][/COLOR][/COLOR][COLOR=#000000]
```
[COLOR=#000000][FONT=monospace]mkdir ~/.config/aacs [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]curl [http://vlc-aacs.whoknowsmy.name/files/KEYDB.cfg](http://vlc-aacs.whoknowsmy.name/files/KEYDB.cfg) > ~/.config/aacs/KEYDB.cfg [/FONT][/COLOR]
```


[/COLOR]
then install [xbmc]("http://wiki.xbmc.org/index.php?title=How-to:Install_XBMC_for_Linux")   and open your    Lebowski bluray   and The Dude should appear :)    best of luck

---

