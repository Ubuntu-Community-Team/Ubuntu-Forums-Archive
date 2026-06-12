---
title: "dr14_tmeter on 18.04"
date: 2018-07-24
forum: Multimedia Software
---

### Post by shantiq on 2018-07-24
Been using  [dr14_tmeter]("https://ubuntuforums.org/showthread.php?t=2379748") for a while on ubuntu 16.04 and I love it.
Now upgraded to 18.04 and it has stopped working and I cannot understand what is missing

this is what I get when I try and use it and the files are there obviously.   ANY ideas

Thanx in advance 

Shan

PS   same message sent to creator/maintainer ...   see who gets there first


```
shan@shan-Aspire-XC-780:~/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]$ dr14_tmeter 
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]


------------------------------------------------------------ 
> Scan Dir: /home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR] 

Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f0b6608eb00>)
Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f0b6608eab8>)

 - ERROR ! 

 - ERROR ! 
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [2].flac: unsupported encoder
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [1].flac: unsupported encoder
- fail - /home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [2].flac
- fail - /home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [1].flac
No audio files found

 Usage: dr14_tmeter [options] path_name 

for more details type 
dr14_tmeter --help

========================

shan@shan-Aspire-XC-780:~/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]$ dr14_tmeter -f The\ Beatles-The\ White\ Album\ \[1\].flac 
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [1].flac

Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f40d80f7638>)

 - ERROR ! 
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]/The Beatles-The White Album [1].flac: unsupported encoder
Error: invalid audio file
```

---

### Post by kazakore on 2018-07-24
> 
flac: unsupported encoder

Is it only flac files it doesn't work with?

It doesn't seem to say what it uses for flac files? What is "flac tool"??

[http://dr14tmeter.sourceforge.net/index.php/Features](http://dr14tmeter.sourceforge.net/index.php/Features)

---

### Post by shantiq on 2018-07-24
well spotted kazakore

works with mp3

```
 dr14_tmeter -f No\ Se.mp3
/home/shan/Music/No Se.mp3

/home/shan/Music/No Se.mp3:      DR 18

/home/shan/Music/No Se.mp3 :
DR      = 18
Peak dB = -0.00
Rms dB  = -21.28


```



so something is amiss with flac    and flac is installed; some other dependency must have got removed during the 16.04>>18.04 upgrade

---

### Post by kazakore on 2018-07-24
As it's not in the repos I can't check the dependencies with apt show, I was going to compare 18.04 with 16.04 but it's not in either. Where did you install it from?

---

### Post by shantiq on 2018-07-24
all explained [here]("https://soundcloud.com/redscarfband")  kazakore.   this was the way in in 16.04

lemme show you the dependencies in synaptic

[ATTACH=CONFIG]280496[/ATTACH][ATTACH=CONFIG]280497[/ATTACH]

---

### Post by mc4man on 2018-07-24
No issue here on 18.04 with  flac, did you try on either a directory or single file that doesn't have such a convoluted path and or name?
Ex.'s
```
$ dr14_tmeter -f /home/doug/Music/03.Summertime.flac
/home/doug/Music/03.Summertime.flac

/home/doug/Music/03.Summertime.flac: 	 DR 10

/home/doug/Music/03.Summertime.flac :
DR      = 10
Peak dB = -1.84
Rms dB  = -17.46
doug@doug-Lenovo-IdeaPad-Y510P:~$ dr14_tmeter -f /home/doug/Music/03.Summertime.flac
/home/doug/Music/03.Summertime.flac

/home/doug/Music/03.Summertime.flac: 	 DR 10

/home/doug/Music/03.Summertime.flac :
DR      = 10
Peak dB = -1.84
Rms dB  = -17.46


doug@doug-Lenovo-IdeaPad-Y510P:~$ dr14_tmeter '/home/doug/Music/Jerry Garcia & David Grisman (1991) Jerry Garcia-David Grisman'
/home/doug/Music/Jerry Garcia & David Grisman (1991) Jerry Garcia-David Grisman


------------------------------------------------------------ 
> Scan Dir: /home/doug/Music/Jerry Garcia & David Grisman (1991) Jerry Garcia-David Grisman 

02 - Grateful Dawg.flac: 	 DR 13
03 - Two Soldiers.flac: 	 DR 12
01 - The Thrill Is Gone.flac: 	 DR 14
04 - Friend Of The Devil.flac: 	 DR 14
05 - Russian Lullaby.flac: 	 DR 14
06 - Dawg's Waltz.flac: 	 DR 14
07 - Walkin' Boss.flac: 	 DR 14
08 - Rockin' Chair.flac: 	 DR 16
09 - Arabia.flac: 	 DR 15
DR = 14

- The full result has been written in the files:  dr14.txt 
- located in the directory: 
/home/doug/Music/Jerry Garcia & David Grisman (1991) Jerry Garcia-David Grisman

Success! 
Elapsed time: 3.88 sec
```

---

### Post by shantiq on 2018-07-25
Hi there Doug


length of name seems to make no difference .    still the unsupported encoder message.   something must have got displaced in the upgrade to 18.04 my guess here. question is what?

```
 dr14_tmeter 
/home/shan/Music/Laibach/2006 - Anglia [CDS]


------------------------------------------------------------ 
> Scan Dir: /home/shan/Music/Laibach/2006 - Anglia [CDS] 

Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f6a31f5c830>)

[COLOR=#ff0000][I] - ERROR ! 
Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f6a31f5c878>)[/I][/COLOR]

 - ERROR ! 
/home/shan/Music/Laibach/2006 - Anglia [CDS]/01-Anglia.flac: unsupported encoder
/home/shan/Music/Laibach/2006 - Anglia [CDS]/02-Espana.flac: unsupported encoder
- fail - /home/shan/Music/Laibach/2006 - Anglia [CDS]/01-Anglia.flac
- fail - /home/shan/Music/Laibach/2006 - Anglia [CDS]/02-Espana.flac
Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f6a31f5c6c8>)

 - ERROR ! 
Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f6a31f5c680>)

 - ERROR ! 
/home/shan/Music/Laibach/2006 - Anglia [CDS]/03-Anglia - Sanctus Mix.[COLOR=#ff0000]*flac: unsupported encoder*[/COLOR]
/home/shan/Music/Laibach/2006 - Anglia [CDS]/04-Espana - El Toreador Mix.flac: unsupported encoder
- fail - /home/shan/Music/Laibach/2006 - Anglia [CDS]/03-Anglia - Sanctus Mix.flac
- fail - /home/shan/Music/Laibach/2006 - Anglia [CDS]/04-Espana - El Toreador Mix.flac
Unexpected error: (<type 'exceptions.IOError'>, IOError(2, 'No such file or directory'), <traceback object at 0x7f6a31f5c5f0>)

 - ERROR ! 
/home/shan/Music/Laibach/2006 - Anglia [CDS]/05-Anglia - Crushed Mix.flac: unsupported encoder
- fail - /home/shan/Music/Laibach/2006 - Anglia [CDS]/05-Anglia - Crushed Mix.flac
No audio files found

 Usage: dr14_tmeter [options] path_name 

for more details type 
dr14_tmeter --help


```

---

### Post by kazakore on 2018-07-25
Try something without whitespace or square brackets anywhere in the path. White space needs to be escaped to work (sometimes not done correctly in scripts) and square brackets get expanded into blobs, kinda like basic regular expressions.

(Although I doubt this is the issue as it seems to show the correct path and filename in the error it may be good to rule it out...)

---

### Post by shantiq on 2018-07-25
ok guys cracked it [and thanx for input]
something big had indeed got displaced/removed/unlinked
ffmpeg  which i install from [here]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")  obviously dr14 reads flac THROUGH ffmpeg but does not mp3 it seems   ...   why it read mp3 and not flac

once ffmpeg reinstalled

```
dr14_tmeter
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]


------------------------------------------------------------ 
> Scan Dir: /home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR] 

The Beatles-The White Album [2].flac:      DR 12
The Beatles-The White Album [1].flac:      DR 11
DR = 12

- The full result has been written in the files:  dr14.txt 
- located in the directory: 
/home/shan/Videos/Transmission Files/The Beatles - The White Album [Cassette XDR]

Success! 
Elapsed time: 24.31 sec


```

---

### Post by Yellow Pasque on 2018-07-27
It uses lame directly when decoding mp3.

[https://github.com/simon-r/dr14_t.meter/blob/7516e5c486be68ad2254d18644f875dffb02f5c8/dr14tmeter/audio_file_reader.py#L163](https://github.com/simon-r/dr14_t.meter/blob/7516e5c486be68ad2254d18644f875dffb02f5c8/dr14tmeter/audio_file_reader.py#L163)

---

### Post by shantiq on 2018-07-27
yes thank you Temüjin and the next entry in the coding confirms that it is ffmpeg that was the issue with my upgrade

[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]class [COLOR=#b22222]FlacFileReader[/COLOR](AudioFileReader):[/TD]
[/TR]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"][/TD]
[/TR]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]    def get_cmd(self):[/TD]
[/TR]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]        return self.get_[COLOR=#ff0000]ffmpeg[/COLOR]_cmd()



[/TD]
[/TR]
[/TABLE]
I never even thought ffmpeg might have got knocked out in the upgrade but knocked out it had been
Ha well you learn as you go along .....    slowly in my case   :]

---

### Post by mc4man on 2018-07-28
If you had followed that ffmpeg guide verbatim then I can't see a release upgrade touching it but it may have been made unusable as the shared libs it used could have changed. ( only 1 failed to find  .so would of caused ffmpeg to not start..

---

