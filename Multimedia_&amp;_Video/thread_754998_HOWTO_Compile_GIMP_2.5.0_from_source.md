---
title: "HOWTO: Compile GIMP 2.5.0 from source"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by odinfromvalhalla on 2008-04-14
Gimp 2.5 came out:

> The most notable change in GIMP 2.5 happened under the hood. The color tools in GIMP have been ported to GEGL. This does not yet have much impact on the user experience but it is a first and important step forward. With full GEGL integration GIMP will finally get support for higher color depths, more colorspaces and eventually non-destructive editing. 

I have posted on my blog a detailed tutorial on how to compile gimp 2.5.0 dev release on Ubuntu Hardy.

URL: [Install GIMP 2.5 on Ubuntu Hard]("http://www.myscienceisbetter.info/2008/04/install-gimp-25-on-ubuntu-hardy.html")

Enjoy!

---

### Post by MetalMusicAddict on 2008-04-17
From a new user's POV I would also put in the HOWTO that the **subversion, ruby** and **libtool** packages will be needed.

**export PKG_CONFIG_PATH=/opt/gimp-2.5/lib/pkgconfig** from section #4 needs to be done before #3.3 will work.

So more like:
> 
**_1. Install the packages needed to compile programs:_**
[LIST]
[*]sudo apt-get install build-essential subversion libtool ruby
[/LIST]

**_2. Install gimp dependencies:_**
[LIST]
[*]sudo apt-get build-dep gimp
[/LIST]

**_3. Install latest BABL and GEGL libs from source_** (these libs were not installed in step 2 as the gimp package in the repo is not depending on them)
[LIST]
[*]svn co [http://svn.gnome.org/svn/babl/trunk/](http://svn.gnome.org/svn/babl/trunk/) babl && svn co [http://svn.gnome.org/svn/gegl/trunk/](http://svn.gnome.org/svn/gegl/trunk/) gegl
[/LIST]

**_3.1 Install BABL:_**
[LIST]
[*]cd babl
[*]./autogen.sh --prefix=/opt/gimp-2.5
[*]make (or "make -j 2" for multiple cores)
[*]sudo make install
[*]cd ..
[/LIST]

**_3.2 Install GEGL:_**
[LIST]
[*]export PKG_CONFIG_PATH=/opt/gimp-2.5/lib/pkgconfig
[*]cd gegl
[*]./autogen.sh --prefix=/opt/gimp-2.5
[*]make (or "make -j 2" for multiple cores)
[*]sudo make install
[*]cd ..
[/LIST]

**_4. Make binaries, includes, libraries in /opt/gimp-2.5 available for use:_**
[LIST]
[*]export PATH=/opt/gimp-2.5/bin:$PATH && export LD_LIBRARY_PATH=/opt/gimp-2.5/lib && export PKG_CONFIG_PATH=/opt/gimp-2.5/lib/pkgconfig
[/LIST]

**_5. Grab GIMP 2.5 tarball._**
[LIST]
[*]wget [ftp://ftp.gimp.org/pub/gimp/v2.5/gimp-2.5.0.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.5/gimp-2.5.0.tar.bz2)
[/LIST]

**_6. Extract and install latest GIMP:_**
[LIST]
[*]tar jxvf gimp-2.5.0.tar.bz2
[*]cd gimp-2.5.0
[*]./configure --prefix=/opt/gimp-2.5
[*]make (or "make -j 2" for multiple cores)
[*]sudo make install
[/LIST]

**_7. Enjoy your GIMP by running:_**
[LIST]
[*]/opt/gimp-2.5/bin/gimp-2.5
[/LIST]


Looking over it, this could actually be scripted rather easily.

---

### Post by MetalMusicAddict on 2008-04-20
Ok. I tinkered some more and if you're really lazy you can simply paste this all into your terminal. Make sure the "source" repo is open in Synaptic 1st.

```
[SIZE="1"]sudo apt-get install build-essential subversion libtool ruby -y && sudo apt-get build-dep gimp -y && svn co http://svn.gnome.org/svn/babl/trunk/ babl && svn co http://svn.gnome.org/svn/gegl/trunk/ gegl && wget ftp://ftp.gimp.org/pub/gimp/v2.5/gimp-2.5.0.tar.bz2 && cd babl && ./autogen.sh --prefix=/opt/gimp-2.5 && make && sudo make install && cd && export PKG_CONFIG_PATH=/opt/gimp-2.5/lib/pkgconfig && cd gegl && ./autogen.sh --prefix=/opt/gimp-2.5 && make && sudo make install && cd && export PATH=/opt/gimp-2.5/bin:$PATH && export LD_LIBRARY_PATH=/opt/gimp-2.5/lib && export PKG_CONFIG_PATH=/opt/gimp-2.5/lib/pkgconfig && tar jxvf gimp-2.5.0.tar.bz2 && cd gimp-2.5.0 && ./configure --prefix=/opt/gimp-2.5 && make && sudo make install && cd[/SIZE]
```

That should do _everything_.

Also, look over the code above. Don't just blindly trust me or anyone. ;) If you have a multi-core system you can replace the "make" part with "make -j <numberofcores>" ie: **make -j 2**.

Launcher:

[LIST]
[*]sudo gedit /usr/share/applications/GIMP-2.5-unstable.desktop
[/LIST]
Paste the text below in and save.

```
[SIZE="1"][Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=GIMP 2.5 (unstable)
GenericName=Image Editor
GenericName[ar]=&#1605;&#1581;&#1585;&#1585; &#1575;&#1604;&#1589;&#1608;&#1585;&#1577;
GenericName[bg]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1085;&#1072; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;
GenericName[ca]=Editor d'imatges
GenericName[cs]=Editor obrázk&#367;
GenericName[da]=Billedredigering
GenericName[de]=Bildeditor
GenericName[dz]=&#3906;&#3935;&#3956;&#3906;&#3942;&#3851;&#3926;&#3938;&#3993;&#3923;&#3851; &#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3924;&#3853;
GenericName[en_CA]=Image Editor
GenericName[en_GB]=Image Editor
GenericName[eo]=Bilada Redaktilo
GenericName[es]=Editor de imagen
GenericName[et]=Pildiredaktor
GenericName[eu]=Irudi-editorea
GenericName[fa]=&#1608;&#1740;&#1585;&#1575;&#1740;&#1588;&#1711;&#1585; &#1578;&#1589;&#1608;&#1740;&#1585;
GenericName[fi]=Kuvaeditori
GenericName[fr]=Éditeur d'image
GenericName[gl]=Editor de imaxes
GenericName[gu]=&#2714;&#2751;&#2724;&#2765;&#2736; &#2744;&#2690;&#2730;&#2750;&#2726;&#2709;
GenericName[hu]=Képszerkeszt&#337;
GenericName[it]=Editor immagine
GenericName[ja]=&#30011;&#20687;&#12456;&#12487;&#12451;&#12479;
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6035;&#6071;&#6038;&#6035;&#6098;&#6034;&#8203;&#6042;&#6076;&#6036;&#6039;&#6070;&#6038;
GenericName[ko]=&#51060;&#48120;&#51648; &#54200;&#51665;&#44592;
GenericName[lt]=Paveiksl&#279;li&#371; rengykl&#279;
GenericName[mk]=&#1059;&#1088;&#1077;&#1076;&#1085;&#1080;&#1082; &#1079;&#1072; &#1089;&#1083;&#1080;&#1082;&#1080;
GenericName[nb]=Bildebehandler
GenericName[ne]=&#2331;&#2357;&#2367; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2325;
GenericName[nl]=Afbeelding-editor
GenericName[pa]=&#2586;&#2623;&#2673;&#2596;&#2608; &#2576;&#2593;&#2624;&#2591;&#2608;
GenericName[pl]=Edytor obrazu
GenericName[pt_BR]=Editor de Imagens
GenericName[ru]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081;
GenericName[sk]=Editor obrázkov
GenericName[sl]=Urejevalnik slik
GenericName[sr]=&#1054;&#1073;&#1088;&#1072;&#1076;&#1072; &#1089;&#1083;&#1080;&#1082;&#1072;
GenericName[sr@Latn]=Obrada slika
GenericName[sv]=Bildredigerare
GenericName[tr]=Resim Düzenleyici
GenericName[tt]=Sürät Tözätkeç
GenericName[uk]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100;
GenericName[vi]=B&#7897; biên so&#7841;n &#7843;nh
GenericName[xh]=UmHleli woMfanekiso
GenericName[zh_CN]=&#22270;&#20687;&#32534;&#36753;&#22120;
GenericName[zh_TW]=&#24433;&#20687;&#32232;&#36655;&#22120;
Comment=Create images and edit photographs
Comment[bg]=&#1057;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1085;&#1077; &#1085;&#1072; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1094;&#1080;&#1103; &#1085;&#1072; &#1089;&#1085;&#1080;&#1084;&#1082;&#1080;
Comment[ca]=Creeu imatges i editeu fotografies
Comment[cs]=Vytvá&#345;et obrázky a upravovat fotografie
Comment[da]=Opret billeder og redigér fotografier
Comment[de]=Bilder erstellen und Fotografien bearbeiten
Comment[dz]=&#3906;&#3935;&#3956;&#3906;&#3942;&#3851;&#3926;&#3938;&#3993;&#3923;&#3851;&#3930;&#3956;&#3851; &#3906;&#3942;&#3938;&#3851;&#3926;&#3942;&#3984;&#4018;&#3956;&#3923;&#3851;&#3936;&#3926;&#3921;&#3851;&#3923;&#3954;&#3851;&#3921;&#3908;&#3851; &#3921;&#3924;&#3938;&#3851;&#3930;&#3956;&#3851;&#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3936;&#3926;&#3921;&#3853;
Comment[en_CA]=Create images and edit photographs
Comment[en_GB]=Create images and edit photographs
Comment[eo]=Kreu bildojn a&#365; redaktu fotojn
Comment[es]=Cree imágenes y edite fotografías
Comment[et]=Loo pilte ja redigeeri fotosid
Comment[eu]=Sortu irudiak eta editatu argazkiak
Comment[fi]=Luo kuvia ja muokkaa valokuvia
Comment[fr]=Crée des images et modifie des photographies
Comment[gl]=Crear imaxes e editar fotografías
Comment[gu]=&#2714;&#2751;&#2724;&#2765;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763; &#2693;&#2728;&#2759; &#2731;&#2763;&#2719;&#2750;&#2707;&#2734;&#2750;&#2690; &#2731;&#2759;&#2736;&#2731;&#2750;&#2736; &#2709;&#2736;&#2763;
Comment[hu]=Képek létrehozása és fotók szerkesztése
Comment[it]=Crea immagini o modifica fotografie
Comment[ja]=&#30011;&#20687;&#12398;&#20316;&#25104;&#12392;&#20889;&#30495;&#12398;&#32232;&#38598;
Comment[km]=&#6036;&#6020;&#6098;&#6016;&#6078;&#6031;&#8203;&#6042;&#6076;&#6036;&#6039;&#6070;&#6038; &#6035;&#6071;&#6020; &#6016;&#6082;&#6047;&#6040;&#6098;&#6042;&#6077;&#6043;&#8203;&#6042;&#6076;&#6036;&#6032;&#6031;
Comment[ko]=&#51060;&#48120;&#51648;&#47484; &#47564;&#46308;&#44144;&#45208; &#49324;&#51652;&#51012; &#54200;&#51665;&#54633;&#45768;&#45796;.
Comment[lt]=Kurti paveiksl&#279;lius ir redaguoti fotografijas
Comment[mk]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080; &#1089;&#1083;&#1080;&#1082;&#1080; &#1080; &#1091;&#1088;&#1077;&#1076;&#1080; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1080;
Comment[nb]=Lag bilder og rediger fotografier
Comment[ne]=&#2331;&#2357;&#2367; &#2360;&#2367;&#2352;&#2381;&#2332;&#2344;&#2366; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381; &#2352; &#2347;&#2379;&#2335;&#2379;&#2327;&#2381;&#2352;&#2366;&#2347; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Comment[nl]=Afbeeldingen of foto's aanmaken en bewerken
Comment[pa]=&#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2579; &#2565;&#2596;&#2631; &#2596;&#2616;&#2613;&#2624;&#2608;&#2622;&#2562; &#2616;&#2635;&#2599;&#2635;
Comment[pl]=Program do tworzenia oraz obróbki obrazów i fotografii
Comment[pt_BR]=Crie e edite imagens ou fotografias
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1081;
Comment[sl]=Ustvari slike in uredi fotografije
Comment[sv]=Skapa bilder och redigera fotografier
Comment[tr]=Resim ya da foto&#287;raflar&#305; olu&#351;turun ve düzenleyin
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1110;&#1081;
Comment[vi]=T&#7841;o và biên so&#7841;n &#7843;nh hay &#7843;nh ch&#7909;p
Comment[zh_CN]=&#21019;&#24314;&#22270;&#20687;&#25110;&#32534;&#36753;&#29031;&#29255;
Comment[zh_TW]=&#24314;&#31435;&#22294;&#20687;&#33287;&#32232;&#36655;&#29031;&#29255;
Exec=/opt/gimp-2.5/bin/gimp-2.5 %U
TryExec=/opt/gimp-2.5/bin/gimp-2.5
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.5
X-GNOME-Bugzilla-OtherBinaries=gimp-2.5
StartupNotify=true
MimeType=image/bmp;image/g3fax;image/gif;image/jpeg;image/jpg;image/pjpeg;image/png;image/tiff;image/x-bmp;image/x-compressed-xcf;image/x-fits;image/x-gray;image/x-pcx;image/x-png;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-sun-raster;image/x-tga;image/x-xbitmap;image/x-xcf;image/x-xpixmap;image/x-xwindowdump;
X-Ubuntu-Gettext-Domain=gimp20
X-Ubuntu-Gettext-Domain=gimp20[/SIZE]
```

---

### Post by odinfromvalhalla on 2008-04-20
nice one :)

I'm sure this will help more people to get gimp 2.5 up and running.

thanks for sharing!

---

### Post by samthurston on 2008-06-30
Thanks for install instructions and especially the launcher.  How can I replace the context menu "open with GIMP Image Editor" ?

---

