---
title: "Recreating CUE."
date: 2012-01-10
forum: Multimedia Software
---

### Post by e-San on 2012-01-10
Hi!

I reconverted whole my lossless collection to flac -8.
I have changed names of files (for one convention).

Now, most of my cue's does not work.
I came to idea to use morituri to check everything with accurip.
But, since I broke my CUEs it is no longer possible.

I would like to recreate cue's with some bash script.

For multi-file albums this should not be a problem (just replace changed names), but what about one-file albums (converted to multi-file)?

I belive i should copy first few lines from original cue (especially those with CD ID) and add list of tracks with filenames. Not sure if lenght is needed...

Can You help me?

Regards!

---

### Post by Vier_ote on 2012-01-11
Use Gedit to rebuild your CUEs files. Take a look to the structure of the files at: 

[http://en.wikipedia.org/wiki/Cue_sheet_(computing)]("http://en.wikipedia.org/wiki/Cue_sheet_(computing)")

There is an example. You don't need legnth but you need the exact time when each track starts and the pregap. Hope to have been useful.

---

### Post by e-San on 2012-01-12
Hi!

There is no problem with modifying it by hand, but i am looking for some bash script (or other language program).

Regards!

---

### Post by Vier_ote on 2012-01-12
The only way I know to make it automatically is through EAC which I have it working under WINE. EAC can generate a CUE sheet processing a **_WAV_** file. But it is not accurate. Sorry!

---

### Post by satanselbow on 2012-01-12
In your very 1st post you state you still have the cue files but they 't tying up with the flacs.

What eactly have you done to these files to make them unusable?

The twinning of cue/flac is usually pretty simple - so information or detail have you destroyed/mutilated that makes it necessary to start from scratch...

Could you maybe post a sample of what you have got? Would make it a lot easier to give a useful answer ;)

---

### Post by e-San on 2012-01-12
Example:

```
san@serwer:/home/publiczny/move/Flac/Zbigniew Preisner (1991 ) The Double Life Of Veronika$ ls
skany
Zbigniew Preisner - The Double Life Of Veronika (La Double Vie De Veronique).cue
Zbigniew Preisner - The Double Life Of Veronika (La Double Vie De Veronique).flac
Zbigniew Preisner - The Double Life Of Veronika (La Double Vie De Veronique).log
```

Thats what i had.

CUE:
```
san@serwer:/home/publiczny/move/Flac/Zbigniew Preisner (1991 ) The Double Life Of Veronika$ cat *cue
REM GENRE Soundtrack
REM DATE 1991
REM DISCID EE074B12
REM COMMENT "ExactAudioCopy v0.99pb5"
PERFORMER "Zbigniew Preisner"
TITLE "The Double Life Of Veronika (La Double Vie De Veronique)"
FILE "Zbigniew Preisner - The Double Life Of Veronika (La Double Vie De Veronique).flac" WAVE
  TRACK 01 AUDIO
    TITLE "Weronika"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 00:00:00
    INDEX 01 00:00:33
  TRACK 02 AUDIO
    TITLE "Veronique"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 00:39:35
    INDEX 01 00:40:70
  TRACK 03 AUDIO
    TITLE "'Tu Viendras'"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 01:05:43
    INDEX 01 01:07:13
  TRACK 04 AUDIO
    TITLE "L'Enfance"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 03:44:60
    INDEX 01 03:46:28
  TRACK 05 AUDIO
    TITLE "Van Den Budenmayer Concerto En Mi Mineur (SBI 152) Version De 1978"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 06:56:33
    INDEX 01 06:58:05
  TRACK 06 AUDIO
    TITLE "Veronique"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 11:27:00
    INDEX 01 11:28:33
  TRACK 07 AUDIO
    TITLE "Solitude"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 12:03:53
    INDEX 01 12:05:53
  TRACK 08 AUDIO
    TITLE "Les Marionnettes"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 13:01:38
    INDEX 01 13:03:73
  TRACK 09 AUDIO
    TITLE "Theme 1re Transcription"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 15:31:58
    INDEX 01 15:33:55
  TRACK 10 AUDIO
    TITLE "L'Enfance II"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 16:28:33
    INDEX 01 16:29:65
  TRACK 11 AUDIO
    TITLE "Alexandre"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 17:28:30
    INDEX 01 17:30:05
  TRACK 12 AUDIO
    TITLE "Alexandre II"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 18:43:55
    INDEX 01 18:45:73
  TRACK 13 AUDIO
    TITLE "Theme 2e Transcription"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 19:58:20
    INDEX 01 20:00:50
  TRACK 14 AUDIO
    TITLE "Concerto En Mi (Instrumentation Contemporaine No.1)"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 20:54:40
    INDEX 01 20:57:03
  TRACK 15 AUDIO
    TITLE "Concerto En Mi (Instrumentation Contemporaine No.2)"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 21:35:55
    INDEX 01 21:37:25
  TRACK 16 AUDIO
    TITLE "Concerto En Mi (Instrumentation Contemporaine No.3)"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 22:51:05
    INDEX 01 22:53:13
  TRACK 17 AUDIO
    TITLE "Van Den Budenmayer Concerto En Mi Mineur (SBI 152) Version De 1802"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 24:18:18
    INDEX 01 24:20:40
  TRACK 18 AUDIO
    TITLE "Generique De Fin"
    PERFORMER "Zbigniew Preisner"
    INDEX 00 29:40:30
    INDEX 01 29:41:55

```

What i do with this is i split 'Zbigniew Preisner - The Double Life Of Veronika (La Double Vie De Veronique).flac' into multiple files (i.e. 01. Zbigniew Preisner - Weronika.flac). 

And for now, first lines from my old_cue:
```
REM GENRE Soundtrack
REM DATE 1991
**REM DISCID EE074B12**
REM COMMENT "ExactAudioCopy v0.99pb5"
PERFORMER "Zbigniew Preisner"
TITLE "The Double Life Of Veronika (La Double Vie De Veronique)"
```

Are useful. For morituri (rip) most and maybe only important line is DISCID and, ofcourse name of files.

So, i need to combine my flac list and old_cue to look like this one:

```
REM GENRE Rock
REM DATE 1994
REM DISCID AA0E3F0C
REM COMMENT "ExactAudioCopy v0.99pb5"
CATALOG 0000000000000
PERFORMER "Voo Voo"
TITLE "Zaplacono"
FILE "01 - Czajnik.wav" WAVE
  TRACK 01 AUDIO
    TITLE "Czajnik"
    PERFORMER "Voo Voo"
    PREGAP 00:00:32
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "Posypalka"
    PERFORMER "Voo Voo"
    INDEX 00 05:43:03
FILE "02 - Posypalka.wav" WAVE
    INDEX 01 00:00:00
  TRACK 03 AUDIO
    TITLE "Lebosklon"
    PERFORMER "Voo Voo"
    INDEX 00 04:14:57
FILE "03 - Lebosklon.wav" WAVE
    INDEX 01 00:00:00
  TRACK 04 AUDIO
    TITLE "Swiat jednonozny"
    PERFORMER "Voo Voo"
    INDEX 00 03:48:10
FILE "04 - Swiat jednonozny.wav" WAVE
    INDEX 01 00:00:00
  TRACK 05 AUDIO
    TITLE "Na polu dzdzy"
    PERFORMER "Voo Voo"
    INDEX 00 03:40:15
FILE "05 - Na polu dzdzy.wav" WAVE
    INDEX 01 00:00:00
  TRACK 06 AUDIO
    TITLE "Grzmotolom I"
    PERFORMER "Voo Voo"
    INDEX 00 06:56:35
FILE "06 - Grzmotolom I.wav" WAVE
    INDEX 01 00:00:00
  TRACK 07 AUDIO
    TITLE "Joszko"
    PERFORMER "Voo Voo"
    INDEX 00 03:06:07
FILE "07 - Joszko.wav" WAVE
    INDEX 01 00:00:00
  TRACK 08 AUDIO
    TITLE "Gdy bede mial 65"
    PERFORMER "Voo Voo"
    INDEX 00 03:36:35
FILE "08 - Gdy bede mial 65.wav" WAVE
    INDEX 01 00:00:00
  TRACK 09 AUDIO
    TITLE "Nawyczkom nie"
    PERFORMER "Voo Voo"
    INDEX 00 05:32:38
FILE "09 - Nawyczkom nie.wav" WAVE
    INDEX 01 00:00:00
  TRACK 10 AUDIO
    TITLE "Lepiej sie dwoiŽc"
    PERFORMER "Voo Voo"
    INDEX 00 03:47:40
FILE "10 - Lepiej sie dwoiŽc.wav" WAVE
    INDEX 01 00:00:00
  TRACK 11 AUDIO
    TITLE "Grzmotolom II"
    PERFORMER "Voo Voo"
    INDEX 00 05:16:72
FILE "11 - Grzmotolom II.wav" WAVE
    INDEX 01 00:00:00
  TRACK 12 AUDIO
    TITLE "Ol Daldi"
    PERFORMER "Voo Voo"
    INDEX 00 07:03:30
FILE "12 - Ol Daldi.wav" WAVE
    INDEX 01 00:00:00

```

Tommorow i'll make some tests to see if cue like thins one:
```
REM DISCID AA0E3F0C
FILE "01 - Czajnik.wav" WAVE
  TRACK 01 AUDIO
    PREGAP 00:00:32
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    INDEX 00 05:43:03
FILE "02 - Posypalka.wav" WAVE
    INDEX 01 00:00:00
```
Wouldn't be enought.

or maybe eaven (lets assume there is no pregap):
```
REM DISCID AA0E3F0C
FILE "01 - Czajnik.wav" WAVE
  TRACK 01 AUDIO
    INDEX 01 00:00:00
  TRACK 02 AUDIO
FILE "02 - Posypalka.wav" WAVE
    INDEX 01 00:00:00
```

So, i only need a script to take disc id, print it to accurip_cue and add track files.

---

### Post by e-San on 2012-01-13
```
REM DISCID E10D4310
FILE "01 - Flota Zjednoczonych Sil.wav" WAVE
  TRACK 01 AUDIO
    PREGAP 00:00:32
    INDEX 01 00:00:00
  TRACK 02 AUDIO
FILE "02 - Ubogi Duchem.wav" WAVE
    INDEX 01 00:00:00
  TRACK 03 AUDIO
FILE "03 - Jak Latwo Zyc.wav" WAVE
    INDEX 01 00:00:00
  TRACK 04 AUDIO
FILE "04 - W Polowie Mniej I.wav" WAVE
    INDEX 01 00:00:00
  TRACK 05 AUDIO
FILE "05 - Nie Dowierzaj.wav" WAVE
    INDEX 01 00:00:00
  TRACK 06 AUDIO
FILE "06 - Lobi Jabi.wav" WAVE
    INDEX 01 00:00:00
  TRACK 07 AUDIO
FILE "07 - Front Torowania Przejsc.wav" WAVE
    INDEX 01 00:00:00
  TRACK 08 AUDIO
FILE "08 - Gusla.wav" WAVE
    INDEX 01 00:00:00
  TRACK 09 AUDIO
FILE "09 - To Nieprawda, Ze Nic Nie Mamy.wav" WAVE
    INDEX 01 00:00:00
  TRACK 10 AUDIO
FILE "10 - W Polowie Mniej II.wav" WAVE
    INDEX 01 00:00:00
  TRACK 11 AUDIO
FILE "11 - Lobi Jabi.wav" WAVE
    INDEX 01 00:00:00
  TRACK 12 AUDIO
FILE "12 - Mydlo, Powidlo.wav" WAVE
    INDEX 01 00:00:00
  TRACK 13 AUDIO
FILE "13 - Papierosy I Gin.wav" WAVE
    INDEX 01 00:00:00
  TRACK 14 AUDIO
FILE "14 - Zatoka Spokojnych Glow.wav" WAVE
    INDEX 01 00:00:00
  TRACK 15 AUDIO
FILE "15 - Koncert.wav" WAVE
    INDEX 01 00:00:00
  TRACK 16 AUDIO
FILE "16 - Dobrze Spij.wav" WAVE
    INDEX 01 00:00:00

```

Gives same output as original cue.
Funny thing, all tracks are Flacs, not waves.

---

### Post by e-San on 2012-08-16
```
san@azazel$ cat lu-cue.sh 
	cat *.cue | grep DISCID
	counter=0

	for i in *.flac; do

		counter=$((counter+1))
		c1=`printf "%02d" $counter`

		echo FILE \"$i\" WAVE
		echo -e "\t TRACK $c1 AUDIO"
		echo -e "\t INDEX 01 00:00:00"

	done
```

```
bash lu-cue.sh > lu.cue
rip image verify lu.cue
```
Works like a charm.

---

