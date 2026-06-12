---
title: "Outputting Mediainfo in a language which is not your system-wide language"
date: 2016-02-20
forum: Multimedia Software
---

### Post by shantiq on 2016-02-20
Always wanted to know how to display Mediainfo output in any language and NOT have to change the system-wide language
So I asked Jerome who is the head honcho for Mediainfo and there is a really ace way of doing that >>




First get the csv file you need [here Brazilian Portuguese]:
```
wget https://raw.githubusercontent.com/MediaArea/MediaInfo/master/Source/Resource/Plugin/Language/pt-BR.csv
```


Then run it thus:




```
mediainfo --Language=file:///home/yourname/pt-BR.csv nameofyourfile
```      




List of languages available
[https://github.com/MediaArea/MediaInfo/tree/master/Source/Resource/Plugin/Language](https://github.com/MediaArea/MediaInfo/tree/master/Source/Resource/Plugin/Language)


**BUT do not** download manually from there download from:


```
wget https://raw.githubusercontent.com/MediaArea/MediaInfo/master/Source/Resource/Plugin/Language/pt-BR.csv
```


just change name of language you wish for...








example:


a mixed ENG/Russian filename read out in French:


```





  mediainfo --Language="file:///home/shantiq/Mediainfo Languages/fr.csv" "/media/extradrive/home/shantiq/Videos/&#1044;&#1101;&#1074;&#1080;&#1076; &#1041;&#1086;&#1091;&#1080; &#1050;&#1086;&#1085;&#1094;&#1077;&#1088;&#1090; &#1074; &#1041;&#1041;&#1057;--2000-David Bowie at the BBC.mp4"
Général
Nom complet                              : /media/extradrive/home/shantiq/Videos/&#1044;&#1101;&#1074;&#1080;&#1076; &#1041;&#1086;&#1091;&#1080; &#1050;&#1086;&#1085;&#1094;&#1077;&#1088;&#1090; &#1074; &#1041;&#1041;&#1057;--2000-David Bowie at the BBC.mp4
Format                                   : MPEG-4
Profil du format                         : Base Media
Identifiant du codec                     : isom
Taille du fichier                        : 635 Mio
Durée                                    : 59mn 5s
Type de débit global                     : Variable
Débit global moyen                       : 1 502 Kbps
Collection                               : David Bowie at the BBC
Album                                    : David Bowie at the BBC
Album/Interprète                         : BBC TV
Piste                                    : David Bowie at the BBC
Groupement                               : Music,Classic Pop & Rock
Interprète                               : BBC Four
Compositeur                              : BBC iPlayer
Genre                                    : Music
Type de contenu                          : TV Show
Description                              : Songs include Ashes to Ashes, Absolute Beginners, The Man Who Sold the World and Fame.
Date d'enregistrement                    : 2012-06-23T00:30:00+01:00
Date d'encodage                          : UTC 1904-01-01 00:00:00
Date de marquage                         : UTC 2012-06-23 19:06:57
Application utilisée                     : Lavf53.21.0
Couverture                               : Yes
Paroles                                  : David Bowie in concert at the BBC Radio Theatre. Songs include Wild is the Wind, Ashes to Ashes, Absolute Beginners, The Man Who Sold the World and Fame. /  / EPISODE /   http://www.bbc.co.uk/iplayer/episode/b01k0y0t/David_Bowie_at_the_BBC/
Commentaire                              : Songs include Ashes to Ashes, Absolute Beginners, The Man Who Sold the World and Fame.
Part_ID                                  : b01k0y0t
TVNetworkName                            : BBC Four


Vidéo
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Profil du format                         : Main@L3
Paramètres du format, CABAC              : Oui
Paramètres du format, RefFrames          : 4 images
Identifiant du codec                     : avc1
Identifiant du codec/Info                : Advanced Video Coding
Durée                                    : 59mn 5s
Type de débit                            : Constant
Débit                                    : 1 404 Kbps
Largeur                                  : 832 pixels
Hauteur                                  : 468 pixels
Format à l'écran                         : 16/9
Type d'images/s                          : Constant
Images par seconde                       : 25,000 Im/s
Norme                                    : PAL
Espace de couleurs                       : YUV
Sous-échantillonnage de la chrominance   : 4:2:0
Profondeur des couleurs                  : 8 bits
Type de balayage                         : Progressif
Bits/(Pixel*Image)                       : 0.144
Taille du flux                           : 592 Mio (93%)
Date d'encodage                          : UTC 1904-01-01 00:00:00
Date de marquage                         : UTC 1904-01-01 00:00:00
Gamme de couleurs                        : Limited


Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Profil du format                         : HE-AAC / LC
Identifiant du codec                     : 40
Durée                                    : 59mn 5s
Type de débit                            : Variable
Débit                                    : 96,0 Kbps
Canaux                                   : 2 canaux
Position des cannaux                     : Front: L R
Echantillonnage                          : 48,0 KHz / 24,0 KHz
Mode de compression                      : Avec perte
Taille du flux                           : 40,0 Mio (6%)
Date d'encodage                          : UTC 1904-01-01 00:00:00
Date de marquage                         : UTC 1904-01-01 00:00:00





```

---

### Post by ajgreeny on 2016-02-20
Whilst on the subject of mediainfo, using Xubuntu I have a custom-action setup in thunar which gives me that info from a right click.

I don't know how easy it is to translate the command from thunar's custom-actions to nautilus or other file-managers, but for information I use command ```
mediainfo -i %f | zenity --text-info
```

A great time-saver!

---

