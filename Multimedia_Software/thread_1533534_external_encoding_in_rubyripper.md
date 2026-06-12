---
title: "external encoding in rubyripper"
date: 2010-07-18
forum: Multimedia Software
---

### Post by shantiq on 2010-07-18
[URL="http://ubuntuforums.org/showthread.php?t=1533534&page=3"][U]THERE IS A SUMMMARY OF ALL INFO FROM THESE 4 PAGES SCROLL 2 THIRDS DOWN PAGE 3 OF THE THREAD
[/URL][/U]

ok [rubyripper ]("http://linuxappfinder.com/package/rubyripper")is designed to be the EAC for linux



and in this thread [here]("http://ubuntuforums.org/showthread.php?t=1531496&page=2") mc4man very kindly gave me the
 other box encode line for mp3HD  slightly modified to give a 320kbps on the lossy aspect of the file


```
mp3hdEncoder  -br 320000 -if "%i" -of "%o".mp3 - -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"

```

[COLOR="Red"]ALSO IMPORTANT
[/COLOR]

MAke sure you have Lame installed on your synaptic the encoding relies on it for the lossy part and make it executable

ALSO make sure you go into the terminal
enter mp3hdEncoder and ACCEPT the agreement

now i am seeking the same information for 3 other formats

i hope some of you know

shorten,wavpack,tta

thank you in advance

---

### Post by lykeion on 2010-07-18
I have no experience with using these formats in rubyripper, 
but Hydrogenaudio Forum seems to be a good place for rubyripper questions. 

Like this thread:
[Ripping+Encoding with RubyRipper and WavPack]("http://www.hydrogenaudio.org/forums/index.php?showtopic=57906")

---

### Post by shantiq on 2010-07-18
cool lykeion

so this is the wavpack line worked perfect first time


```
wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"
```


anyone got clues on shorten?

---

### Post by mc4man on 2010-07-18
this will get you started with tta, for tagging a bit of research and experimenting - could get convoluted.  

```
ttaenc -e  "%i" -o "%o".tta 
```

You should edit the commin post 1

---

### Post by shantiq on 2010-07-18
thank you for tta    works like a dream


changed the mp3HD line above to the new one



still stumped on shorten    all i know is that in EAC one needs no added command line instructions simply the path of the plugin

---

### Post by mc4man on 2010-07-18
As in the other thread my last post  - the comm. for mp3hd needs a .mp3
(then you'll get a .mp3 ext and -mode 1 will be passed to encoder instead of 1

as in 
```
mp3hdEncoder -if "%i" -of "%o"[COLOR="Red"].mp3[/COLOR] -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```

Edit = see you got what I mean - off to sleep....

---

### Post by shantiq on 2010-07-18
3 so far


wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"


mp3hdEncoder -if "%i" -of "%o".mp3 -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"



ttaenc -e  "%i" -o "%o".tta


this is pleasing


```
shantiq@shantiq-desktop:~$ rrip_cli 
Scanning disc with cdrdao
Audio-disc found, number of tracks : 4, total playlength : 47:55
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: Ashra
Album: New Age Of Earth
Genre: Progressive Rock
Year: 1976

TRACK INFO
1) Sunrain
2) Ocean of Tenderness
3) Deep Distance
4) Nightdust

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] ttaenc -e "%i" -o "%o".tta
/home/shantiq/other/Ashra (1976) New Age Of Earth
Ashra - New Age Of Earth (1976).tta
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> ttaenc -e "%i" -o "%o"

CDDB INFO

Artist	= Ashra
Album	= New Age Of Earth
Year	= 1976
Genre	= Progressive Rock
Tracks	= 4 (1 selected)


ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while

Loading file: /tmp/temp_cdrom.toc
Disc type = CD_DA
Found info of tracknumber 1
Found info of tracknumber 2
Found info of tracknumber 3
Found info of tracknumber 4
Debug info: gaps are now prepended
Startsector	Lengthsector
0	33661
33661	56980
90641	26502
117143	98524
Silence detected for track 1 : 32 sectors
Pregap detected for track 1 : 32 sectors
Pregap detected for track 2 : 316 sectors
Pregap detected for track 3 : 536 sectors
Pregap detected for track 4 : 259 sectors


STATUS

Ripping progress (0 %)
Ripping image
Expected filesize for image		is 507248828 bytes.
Free disk space is 403861464 MB
Minutes ripping is 0.000469833333333333.
Starting to rip CD image, trial #1cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_1.wav" 2>&1
 (297 seconds)
Minutes ripping is 4.95730121666667.
Starting to rip CD image, trial #2cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_2.wav" 2>&1
 (295 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 2810439c68d648929e9847b806b9d58e

Ripping progress (100 %)
Encoding progress (0 %)
Adding track image (other) to the queue..
command = ttaenc -e "/home/shantiq/other/temp_sr0/image_1.wav" -o "/home/shantiq/other/Ashra (1976) New Age Of Earth/Ashra - New Age Of Earth (1976).tta"
TTA1 lossless audio encoder/decoder, release 3.4.1
Copyright (c) 2007 Aleksander Djuric. All rights reserved.
For more information see http://tta.sourceforge.net
------------------------------------------------------------
File:	[image_1.wav]
Encode:	complete, wrote 248138047 bytes, ratio: 0.49, time: 36
------------------------------------------------------------
Total:	[1/1, 236.6/483.8 Mb], ratio: 0.489, time: 0'36
------------------------------------------------------------

Encoding progress (100 %)
Removing track image (other) from the queue..
Inside the finished function
Encoding progress (100 %)

```

---

### Post by shantiq on 2010-07-18
this below is all the info i have on shorten i tried a few things and got nowhere useful


```
shorten version 3.6.1: (c) 1992-1999 Tony Robinson and SoftSound Ltd
Seek extensions by Wayne Stielau; UNIX maintenance by Jason Jordan
Usage: shorten {options} [input file] [output file]
  -a 0     bytes to copy verbatim to align file
  -b 256   block size
  -c 1     number of channels
  -d 0     number of bytes to discard before compression or decompression
  -e       erase seek table appended to input file
  -h       help (this message)
  -i       inquire as to whether a seek table is appended to input file
  -k       append seek table information to existing shorten file
  -l       print the license giving the distribution and usage conditions
  -m 4     number of past block for mean estimation
  -n 256   minimum signal to noise ratio in dB (256 == lossless coding)
  -p 0     maximum LPC predictor order (0 == fast polynomial predictor)
  -q 0     acceptable quantisation error in bits
  -r 32.0  maximum number of bits per sample (32.0 == lossless coding)
  -s       generate seek table information in separate file [input file].skt
  -S[name] generate seek table information in separate file given by [name]
  -t wav   specify the bit packing and byte ordering of the sample file from
           {aiff,wav,ulaw,alaw,s8,u8,s16,u16,s16x,u16x,s16hl,u16hl,s16lh,u16lh}
  -u       merge the two zero codes in ulaw files
  -v 3     format version number (2: no seek info; 3: default)
  -x       extract (all other options except -a, -d and -t are ignored)

```

```
SHORTEN(1)
local
SHORTEN(1)
NAME
shorten &#8722; fast compression for waveform files
SYNOPSIS
shorten [-hlu] [-a #bytes] [-b #samples] [-c #channels] [-d #bytes] [-m #blocks] [-n #dB] [-p #order] [-q
#bits] [-r #bits] [-t filetype] [-v #version] [waveform-file [shortened-file]]
shorten -x [-hl] [ -a #bytes] [-d #bytes] [shortened-file [waveform-file]]
shorten [ -e | -i | -k | -s | -S<name> ] shortened-file
shorten [ -s | -S<name> ] < shortened-data
DESCRIPTION
shorten reduces the size of waveform files (such as audio) using Huffman coding of prediction residuals
and optional additional quantisation. In lossless mode the amount of compression obtained depends on the
nature of the waveform. Those composing of low frequencies and low amplitudes give the best compres-
sion, which may be 2:1 or better. Lossy compression operates by specifying a minimum acceptable seg-
mental signal to noise ratio or a maximum bit rate. Lossy compression operates by zeroing the lower order
bits of the waveform, so retaining waveform shape.
If both file names are specified then these are used as the input and output files. The first file name can be
replaced by "-" to read from standard input and likewise the second filename can be replaced by "-" to write
to standard output. Under UNIX, if only one file name is specified, then that name is used for input and the
output file name is generated by adding the suffix ".shn" on compression and removing the ".shn" suffix on
decompression. In these cases the input file is removed on completion. The use of automatic file name
generation is not currently supported under DOS. If no file names are specified, shorten reads from stan-
dard input and writes to standard output. Whenever possible, the output file inherits the permissions,
owner, group, access and modification times of the input file.
From release 2.3 the RIFF WAVE (Microsoft .wav) file type is the default. These files contain enough
information to set most of the switches presented below, so effective operation is obtained just by setting
the desired level of compression (-n or -r switch).
OPTIONS
&#8722;a align bytes
Specify the number of bytes to be copied verbatim before compression begins. This option can be
used to preserve fixed length ASCII headers on waveform files, and may be necessary if the header
length is an odd number of bytes.
&#8722;b block size
Specify the number of samples to be grouped into a block for processing. Within a block the sig-
nal elements are expected to have the same spectral characteristics. The default option works well
for a large range of audio files.
&#8722;c channels
Specify the number of independent interwoven channels. For two signals, a(t) and b(t) the original
data format is assumed to be a(0),b(0),a(1),b(1)...
&#8722;d discard bytes
Specify the number of bytes to be discarded before compression or decompression. This may be
used to delete header information from a file. Refer to the -a option for storing the header infor-
mation in the compressed file.
&#8722;e Erase seek information from an existing file.
&#8722;h Give a short message specifying usage options.
&#8722;i Inquire as to whether the given file is an external seek table file, a file with seek tables appended to
          it, or neither. If seek tables are present, the seek table revision number is shown.
&#8722;k Append seek information to an existing file.
shorten 3.6.1
March 2007
1
SHORTEN(1)
&#8722;l
local
SHORTEN(1)
Prints the software license specifying the conditions for the distribution and usage of this software.
&#8722;m blocks
Specify the number of past blocks to be used to estimate the mean and power of the signal. The
value of zero disables this prediction and the mean is assumed to lie in the middle of the range of
the relevant data type (i.e. at zero for signed quantities). The default value is non-zero for format
versions 2.0 and above.
&#8722;n noise level
Specify the minimum acceptable segmental signal to noise ratio in dB. The signal power is taken
as the variance of the samples in the current block. The noise power is the quantisation noise
incurred by coding the current block assuming that samples are uniformally distributed over the
quantisation interval. The bit rate is dynamically changed to maintain the desired signal to noise
ratio. The default value represents lossless coding.
&#8722;p prediction order
Specify the maximum order of the linear predictive filter. The default value of zero disables the
use of linear prediction and a polynomial interpolation method is used instead. The use of the lin-
ear predictive filter generally results in a small improvement in compression ratio at the expense of
execution time. This is the only option to use a significant amount of floating point processing
during compression. Decompression still uses a minimal number of floating point operations.
Decompression time is normally about twice that of the default polynomial interpolation. For ver-
sion 0 and 1, compression time is linear in the specified maximum order as all lower values are
searched for the greatest expected compression (the number of bits required to transmit the predic-
tion residual is monotonically decreasing with prediction order, but transmitting each filter coeffi-
cient requires about 7 bits). For version 2 and above, the search is started at zero order and termi-
nated when the last two prediction orders give a larger expected bit rate than the minimum found
to date. This is a reasonable strategy for many real world signals - you may revert back to the
exhaustive algorithm by setting -v1 to check that this works for your signal type.
&#8722;q quantisation level
Specify the number of low order bits in each sample which can be discarded (set to zero). This is
useful if these bits carry no information, for example when the signal is corrupted by noise.
&#8722;r bit rate
Specify the expected maximum number of bits per sample. The upper bound on the bit rate is
achieved by setting the low order bits of the sample to zero, hence maximising the segmental sig-
nal to noise ratio.
&#8722;s
Write seek table information to a separate file (uses shortened file name with ’.skt’ extension). If
the shortened data is read from standard input, then the seek table information will be saved in
’stdin.skt’.
&#8722;S<name>
Write seek table information to a separate file given by "<name>".
&#8722;t file type
Gives the type of the sound sample file as one of aiff, wav, s8, u8, s16, u16, s16x, u16x, s16hl,
u16hl, s16lh, u16lh, ulaw, or alaw.
The simple types are listed first and have an initial s or u for signed or unsigned data, followed by
8 or 16 as the number of bits per sample. No further extension means the data is in the natural
byte order, a trailing x specifies byte swapped data, hl explicitly states the byte order as high byte
followed by low byte and lh the converse. Hence s16 means signed 16 bit integers in the natural
byte order (like C would fwrite() shorts).
ulaw is the natural file type of ulaw encoded files (such as the default sun .au files) and alaw is a
similar byte-packed scheme. Specific optimisations are applied to ulaw and alaw files. If lossless
shorten 3.6.1
March 2007
2
SHORTEN(1)
local
SHORTEN(1)
compression is specified with ulaw files then a check is made that the whole dynamic range is used
(useful for files recorded on a SparcStation with the volume set too high). Lossless coding of both
file types uses an internal format with a monotonic mapping to linear. If lossy compression is
specified then the data is internally converted to linear. The lossy option "-r4" has been observed
to give little degradation and provides 2:1 compression.
With the types listed above you should explicitly set the number of channels (if not mono) with -c
and if the file contains a header the size should be specified with -a. This is most important for
lossy compression which will lead to data corruption if a file header is inadvertently lossy coded.
Finally, as of version 2.3, the file type may be specified as wav (the default). In this case the file to
be compressed is interogated for the specific data type (chosen from the above) and the number of
channels to be used. The header length alignment (-a flag) is also automatic so lossless compres-
sion requires no switches to be set and lossy compression requires only that the compression level
be set with -n or -r.
&#8722;u
The ulaw standard (ITU G711) has two codes which both map onto the zero value on a linear
scale. The "-u" flag maps the negative zero onto the positive zero and so yields marginally better
compression for format version 2 (the gain is significant for older format versions).
&#8722;v version
Specify the binary format version number of compressed files. Legal values are currently 1, 2 and
3, with higher numbers generally giving better compression. 2 and 3 are identical, with the excep-
tion that 2 does not generate seek tables, while 3 does. Detection of format version on decode is
automatic.
&#8722;x extract
Reconstruct the original file. All other command line options except -a and -d are ignored.
METHODOLOGY
shorten works by blocking the signal, making a model of each block in order to remove temporal redun-
dancy, then Huffman coding the quantised prediction residual.
Blocking
The signal is read in a block of about 128 or 256 samples, and converted to integers with expected mean of
zero. Sample-wise-interleaved data is converted to separate channels, which are assumed independent.
Decorrelation
Four functions are computed, corresponding to the signal, difference signal, second and third order differ-
ences. The one with the lowest variance is coded. The variance is measured by summing absolute values
for speed and to avoid overflow.
Compression
It is assumed the signal has the Laplacian probability density function of exp(-abs(x)). There is a computa-
tionally efficient way of mapping this density to Huffman codes, The code is in four parts: a run of zeros; a
bounding one; a fixed number of bits mantissa; and the sign bit. The number of leading zeros gives the off-
set from zero. Some examples for a 2 bit mantissa:
Value zeros stopbit mantissa signbit total code
0
1
00
0
1000
1
1
01
0
1010
2
1
10
0
1010
4
0
1
00
0
01000
7
0
1
11
0
01110
8
00 1
00
0
001000
shorten 3.6.1
March 2007
3
SHORTEN(1)
local
-1
-2
-7
0
1
1
1
00
01
10
1
1
1
SHORTEN(1)
1001
1011
01101
Note that negative numbers are offset by one as there is no need to have two zero codes. The technical
report CUED/F-INFENG/TR.156 included with the shorten distribution as files tr154.tex and tr154.ps con-
tains bugs in this format description and is superceeded by this man page.
EMBEDDED OPERATION
Shorten may be used embedded within other programs. shorten is a function call implemented in the file
shorten.c. The file main.c provides a wrapper for stand alone operation. A simple example of ebedded
operation can be found in the file embedded.c. Full windows DLL operation is provided in the windll sub-
directory.
SEE ALSO
compress(1),pack(1).
DIAGNOSTICS
Exit status is normally 0. A warning is issued if the file is not properly aligned, i.e. a whole number of
records could not be read at the end of the file.
BUGS
An easy way to test shorten for your system is to use "make check", if this fails, for whatever reason, please
report it to <shnutils@freeshell.org>.
No check is made for increasing file size, but valid waveform files generally achieve some compression.
Even compressing a file of random bytes (which represents the worst case waveform file) only results in a
small increase in the file length (about 6% for 8 bit data and 3% for 16 bit data). There is one condition
that is know to be problematic, that is the lossy compression of unsigned data without mean estimation -
large file sizes may result if the mean is far from the middle range value. For these files the value of the -m
switch should be non-zero, as it is by default in format version 2.
There is no provision for different channels containing different data types. Normally, this is not a restric-
tion, but it does mean that if lossy coding is selected for the ulaw type, then all channels use lossy coding.
The technical report CUED/F-INFENG/TR.156 (included in the shorten distribution) report contains errors
in the bitfield format description and is superceeded by this document.
See the file "ChangeLog" for a history of bug fixes and feature additions.
Please mail Jason Jordan at the address below if you find a bug in shorten involving seek tables.
Please mail Brian Willoughby at the address below if you find a bug in the AIFF implementation.
Please mail Tony Robinson immediately at the address below if you find a bug in shorten that is NOT
related to seek tables or AIFF support. Make sure you can reproduce your bug using version 2.3a, the last
version known to be released by him.
AVAILABILITY
The latest 2.x and 3.x versions can be obtained from <http://www.etree.org/shnutils/shorten/> or
<http://shnutils.freeshell.org/shorten/>.
AUTHORS
Copyright (C) 1992-1999 by Tony Robinson and SoftSound Ltd (ajr@softsound.com)
Unix maintenance of 3.x versions by Jason Jordan <shnutils@freeshell.org>.
AIFF support and maintenance by Brian Willoughby <shorten@sounds.wa.com> of Sound Consulting
<http://sounds.wa.com/>.
shorten 3.6.1
March 2007
4
SHORTEN(1)
local
SHORTEN(1)
Shorten is available for non-commercial use without fee. See the LICENSE file for the formal copying and
usage restrictions. For supported versions please see http://www.softsound.com/Shorten.html and for com-
mercial use please contact shorten@softsound.com
shorten 3.6.1
March 2007
5

```

---

### Post by mc4man on 2010-07-18
it appears difficult for shorten in rr, may require some add. to rr script

Another way is to use soundkonverter
Put 'shorten' in path (assume you already have

Open sk.'s settings -> configure sk.-> backends

Confirm it found shorten (screen1

At top switch to either cdparanoia or cdda2wav 
(if using cdda2wav suggest not usinf debian/ubuntu version but latest, can describe how - screen 2

Then close and reopen sk. (if not the ripping backend will not be set, on subsquent rips do d. check it hasn't been set back to kde...

then open and add from 'file' -> use the button - screen 3

---

### Post by shantiq on 2010-07-18
hi mc4man


i already have everything in sk for shn

or use shntool for conversion


i can also rip to shorten with pacpl but not the secure way rr offers

EAC does it too under wine


i would have thought there must be a line that can be entered in the other box

unless there are technical impossibilities there which i do not understand

anyway again thank you

---

### Post by mc4man on 2010-07-18
posting an issue here may at some point provide some info
[http://code.google.com/p/rubyripper/issues/list](http://code.google.com/p/rubyripper/issues/list)

(because rr crashes vs. fails to encode it would appear to be a 'tech' issue than comm. structure

---

### Post by shantiq on 2010-07-18
will do.



[there]("http://code.google.com/p/rubyripper/issues/detail?id=434")

---

### Post by shantiq on 2010-07-19
ok so i used this i cobbled together

shorten "%i" -o "%o" .shn


and got to here

```
Ripping track 9
Expected filesize for track 9		is 52630748 bytes.
shorten: too many filenames
shorten: for more information use: shorten -h
WARNING: Encoding to other exited with an error with track 8!
Free disk space is 407176312 MB
Minutes ripping is 7.22746876666667.
[COLOR="DarkRed"]Encoding progress (45.5 %)[/COLOR]
Starting to rip track 9, trial #1cdparanoia [.151799]-[.22376] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track9_1.wav" 2>&1
Removing track 8 (other) from the queue..
 (24 seconds)
Minutes ripping is 7.6340016.

```


not there yet but cannot be far

---

### Post by mc4man on 2010-07-19
You know, when I was trying, (using the gui), I kept forgetting to add the .shn - that's why rr was crashing(exiting really) here.

In your Ex. where it stops at track 9,  how many tracks are on the cd? ie. was track 8 the last track?

Edit;

Just did a cd w/18 tracks, none where skipped or caused the encoder to exit

---

### Post by shantiq on 2010-07-19
> **mc4man said:**
> You know, when I was trying, (using the gui), I kept forgetting to add the .shn - that's why rr was crashing(exiting really) here.

In your Ex. where it stops at track 9,  how many tracks are on the cd?


Hi Mc

sorry i cannot remember i tried a few discs:KS
but
no it does not crash at any point it simply does not complete the encode  i think it just needs minor tweeking

someone somewhere must know


i personally do not have much technical knowledge


i have written to this guy here


> AUTHORS
       Copyright (C) 1992-1999 by Tony Robinson and SoftSound  Ltd  (ajr@soft&#8208;
       sound.com)

       Unix   maintenance   of   3.x   versions   by  **[COLOR="Red"] Jason   Jordan  [/COLOR]** <shnu&#8208;
       [email]tils@freeshell.org[/email]>.

       AIFF    support     and     maintenance     by     Brian     Willoughby
       <shorten@sounds.wa.com> of Sound Consulting <http://sounds.wa.com/>.

       Shorten  is  available  for  non-commercial  use  without fee.  See the
       LICENSE file for the formal copying and usage restrictions.   For  sup&#8208;
       ported  versions  please  see [http://www.softsound.com/Shorten.html](http://www.softsound.com/Shorten.html) and
       for commercial use please contact [email]shorten@softsound.com[/email]
   asking for advice

i am convinced that it is a really simple line since in EAC it needs no extra command line coding and EVERY other codec does


  see

under Wine


[CENTER][IMG]http://img835.imageshack.us/img835/4816/compressionoptions014.png[/IMG][/CENTER]



much info     [http://www.etree.org/index.html](http://www.etree.org/index.html)


[http://etree.org/linux.html](http://etree.org/linux.html)

---

### Post by mc4man on 2010-07-19
Hmm, as my edit just did a large cd (18 trk), with no issue's at all w/ shorten

Maybe try that disk again (the log should be in album folder to find the one that failed)
If you find which cd then also try to rip just tr. 8 and see

---

### Post by shantiq on 2010-07-19
ok got the answer from 2 sources


Jason Jordan and also mc3...@optonline.net ( mc4man ) [here]("http://code.google.com/p/rubyripper/issues/detail?id=434")


and the answer is    ```
shorten "%i" "%o".shn

```


and yes it is simple as it is in EAC where no code is added but is is nice now to know one can do a secure rip to shorten in Linux 

with a Linux ripper


truly chuffed:KS:KS     Thanx for all help received


ps   shorten plays in audacious/xmms/xmms2   and probably others i do not know



```
shantiq@shantiq-desktop:~$ rrip_cli 
Audio-disc found, number of tracks : 7, total playlength : 73:30
Fetching freedb info...
Scanning disc with cdrdao

FREEDB INFO

DISC INFO
Artist: Can
Album: Tago Mago
Genre: Unknown
Year: 2004

TRACK INFO
1) Paperhouse
2) Mushroom
3) Oh Yeah7-04-20603v®
4) Halleluwah
5) Aumgn
6) Peking O
7) Bring Me Coffee Or Tea

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] shorten  "%i"  "%o".shn
/home/shantiq/other/Can (2004) Tago Mago
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] /home/shantiq/other/Can (2004) Tago Mago#3
Can - Tago Mago (2004).shn
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> shorten  "%i"  "%o"

CDDB INFO

Artist	= Can
Album	= Tago Mago
Year	= 2004
Genre	= Unknown
Tracks	= 7 (1 selected)


ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while

Loading file: /tmp/temp_cdrom.toc
Disc type = CD_DA
Found cd_text for disc
Found artist for disc: "TAGO MAGO"
Found album for disc: 
Found info of tracknumber 1
CD-text found: Title = Paperhouse
Found info of tracknumber 2
CD-text found: Title = Mushroom
Found info of tracknumber 3
CD-text found: Title = Oh Yeah
Found info of tracknumber 4
CD-text found: Title = Halleluwah
Found info of tracknumber 5
CD-text found: Title = Aumgn
Found info of tracknumber 6
CD-text found: Title = Peking O
Found info of tracknumber 7
CD-text found: Title = Bring Me Coffee Or Tea
Debug info: gaps are now prepended
Startsector	Lengthsector
0	33667
33667	18268
51935	33165
85100	83370
168470	78870
247340	52747
300087	30690
Pregap detected for track 4 : 67 sectors
Pregap detected for track 5 : 152 sectors
Pregap detected for track 6 : 572 sectors
Pregap detected for track 7 : 165 sectors


STATUS

Ripping progress (0 %)
Ripping image
Expected filesize for image		is 777987548 bytes.
Free disk space is 403660796 MB
Minutes ripping is 0.000395983333333333.
Starting to rip CD image, trial #1cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_1.wav" 2>&1
 (381 seconds)
Minutes ripping is 6.36351268333333.
Starting to rip CD image, trial #2cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_2.wav" 2>&1
 (380 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 791f1a6927bc95c7450bc7072a783dd8

Ripping progress (100 %)
Encoding progress (0 %)
Adding track image (other) to the queue..
command = shorten  "/home/shantiq/other/temp_sr0/image_1.wav"  "/home/shantiq/other/Can (2004) Tago Mago#3/Can - Tago Mago (2004).shn"
appending seek table to '/home/shantiq/other/Can (2004) Tago Mago#3/Can - Tago Mago (2004).shn'
Encoding progress (100 %)
Removing track image (other) from the queue..
Inside the finished function
Encoding progress (100 %)


```

---

### Post by mc4man on 2010-07-20
for alac - one way, no tags (will try something tomorrow about that

Have a decent ffmpeg installed, then in 'other'

```
ffmpeg -i %i -acodec alac  "%o".m4a
```

---

### Post by shantiq on 2010-07-20
:KS quick work  :KS thank you will try straight away

i see this is the code one uses in ffmpeg


Works perfect will add to the howto below


and this is one up on EAC where you have to link to the codec inside an installed version of itunes (which i do not really want on my machine) for it to work

so rubyripper is more efficient on alac     first successful rip ever to alac using ubuntu:KS


```
shantiq@shantiq-desktop:~$ rrip_cli 
Scanning disc with cdrdao
Audio-disc found, number of tracks : 24, total playlength : 72:51
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: Various Artists
Album: Gypsy Caravan
Genre: Soundtrack
Year: 2007

TRACK INFO
1) Tientos Tangos
2) Gypsy/No Gypsy
3) Nicoleta
4) Smoking Bass
5) Romano Horo
6) Spoons
7) Carolina
8) Maro Jailo Remix
9) Roomal
10) Te Necesito
11) Feria Feet
12) Desert Night Journey
13) Rajasthani Rap
14) Hora cu strigaturii
15) Cantinas
16) Kimero
17) Mehndi O Malir
18) Market Moment
19) Nakalavishe
20) Asfalt Tango
21) Mugur, mugurel
22) Hajre Mate Diki Daje
23) Jasmina Dromoro
24) Djelem Djelem

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] ffmpeg -i "%i" -acodec alac  "%o".m4a
/home/shantiq/other/Various Artists (2007) Gypsy Caravan
Various Artists - Gypsy Caravan (2007).m4a
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> ffmpeg -i "%i" -acodec alac  "%o"

CDDB INFO

Artist	= Various Artists
Album	= Gypsy Caravan
Year	= 2007
Genre	= Soundtrack
Tracks	= 24 (1 selected)


ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while

Loading file: /tmp/temp_cdrom.toc
Disc type = CD_DA
Found info of tracknumber 1
Found info of tracknumber 2
Found info of tracknumber 3
Found info of tracknumber 4
Found info of tracknumber 5
Found info of tracknumber 6
Found info of tracknumber 7
Found info of tracknumber 8
Found info of tracknumber 9
Found info of tracknumber 10
Found info of tracknumber 11
Found info of tracknumber 12
Found info of tracknumber 13
Found info of tracknumber 14
Found info of tracknumber 15
Found info of tracknumber 16
Found info of tracknumber 17
Found info of tracknumber 18
Found info of tracknumber 19
Found info of tracknumber 20
Found info of tracknumber 21
Found info of tracknumber 22
Found info of tracknumber 23
Found info of tracknumber 24
Debug info: gaps are now prepended
Startsector	Lengthsector
0	20850
20850	2216
23066	17111
40177	2440
42617	12741
55358	1818
57176	24294
81470	15256
96726	20459
117185	13232
130417	2017
132434	14032
146466	2425
148891	10682
159573	24164
183737	27895
211632	5174
216806	1588
218394	13324
231718	21227
252945	22418
275363	21797
297160	24699
321859	6039
Pregap detected for track 3 : 40 sectors
Pregap detected for track 6 : 21 sectors
Pregap detected for track 10 : 101 sectors
Pregap detected for track 16 : 64 sectors
Pregap detected for track 22 : 159 sectors
Pregap detected for track 23 : 101 sectors


STATUS

Ripping progress (0 %)
Ripping image
Expected filesize for image		is 771216140 bytes.
Free disk space is 402713380 MB
Minutes ripping is 0.000314366666666667.
Starting to rip CD image, trial #1cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_1.wav" 2>&1
 (362 seconds)
Minutes ripping is 6.04984995.
Starting to rip CD image, trial #2cdparanoia [.0]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/image_2.wav" 2>&1
 (363 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 7410adf055d76dfbba5c2f4ffbb741f9

Ripping progress (100 %)
Encoding progress (0 %)
Adding track image (other) to the queue..
command = ffmpeg -i "/home/shantiq/other/temp_sr0/image_1.wav" -acodec alac  "/home/shantiq/other/Various Artists (2007) Gypsy Caravan/Various Artists - Gypsy Caravan (2007).m4a"
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, wav, from '/home/shantiq/other/temp_sr0/image_1.wav':
  Duration: 01:12:51.97, bitrate: 1411 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Output #0, ipod, to '/home/shantiq/other/Various Artists (2007) Gypsy Caravan/Various Artists - Gypsy Caravan (2007).m4a':
    Stream #0.0: Audio: alac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=  431386kB time=4372.04 bitrate= 808.3kbits/s    
video:0kB audio:431018kB global headers:0kB muxing overhead 0.085468%
Encoding progress (100 %)
Removing track image (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ 

```

---

### Post by shantiq on 2010-07-20
**how to__**


so to summarize to rip with rubyripper with external encoders one needs to take the following steps


1.   download the codecs

[for tta ]("http://sourceforge.net/projects/tta/files/tta/ttaenc-src/ttaenc-3.4.1-src.tgz/download") 

for shorten  shorten 3.6.1  (attached below)

for [mp3HD]("http://www.all4mp3.com/Download.aspx?eula=mp3hd_eula.html&file=mp3HD_Toolkit_for_Linux_2010-02-02.zip&name=Linux%20mp3HD%20Toolkit%20for%20v1.5") from [http://www.all4mp3.com/SoftwareHD.aspx](http://www.all4mp3.com/SoftwareHD.aspx)    
(also attached)


for alac   install ffmpeg from repository/synaptic



2.Then they need to be made executable  once installed they need to go to


/usr/bin     and-or   /usr/local/bin

so find them on your computer  

and move them and change ownership   with these lines


```
sudo cp mp3hdEncoder /usr/local/bin

```

```
sudo cp mp3hdEncoder /usr/bin

```


```
sudo chown username mp3hdEncoder

```

[COLOR="DarkRed"]Change encoder name accordingly
[/COLOR]
and click allow executing file by right clicking on the file and checking properties


[CENTER][IMG]http://img686.imageshack.us/img686/5333/mp3hdencoderproperties0.png[/IMG]
[/CENTER]

3.   now we can go to rubyripper bring up from terminal with
```
rrip_gui 
```  go preferences/codecs


Tick other box (untick all others if you want to rubyripper allows multiple encoding)

and then write the appropriate code line


```
shorten  "%i" "%o".shn

```


```
wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"
```


```
mp3hdEncoder -if "%i" -of "%o".mp3 -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```



```
ttaenc -e  "%i" -o "%o".tta
```


```
ffmpeg -i %i -acodec alac  "%o".m4a

```

(alac plays in [deadbeef]("http://ubuntuforums.org/showthread.php?t=1503749"))


4.finally  close gui   write ```
rrip_cli
``` in terminal and follow steps which are REALLY clear


And now you have a secure copy done entirely with Linux/Ubuntu

njoi!      ( all info from Mc4man )

---

### Post by mc4man on 2010-07-20
got tagging with alac, small caveat - 
The  album folder will be created in 2 places - ~/other, which will contain the log and a .m3u (didn't try cue

The encodes will be in ~/tmp/m4a/<album name> and due to a small issue with atomicparsley will have a .aac ext (really are .m4a's - will look into

No big deal - can be moved back into 'other' and you can use a batch rename command to make ext .m4a

command is quite large and requires atomicparsley to be installed

comm. (change blue to your username - 2 places

```
ffmpeg  -i %i -acodec alac  "%o".m4a && mkdir -p /home/[COLOR="Blue"]doug[/COLOR]/tmp/m4a/%a\ \(%y\)\ %b && AtomicParsley "%o".m4a -o /home/[COLOR="Blue"]doug[/COLOR]/tmp/m4a/%a\ \(%y\)\ %b/%n\ -\ %t.aac --artist "%a" --album "%b" --tracknum "%n" --year "%y" --title "%t"  --genre "%g" && rm "%o".m4a

```

**Don't copy command from below quote**
> 
This log is created by Rubyripper, version 0.6.0
Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
ATAPI DVD A  DH20A4P 9P59
Cdrom offset used: 0

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> ffmpeg  -i "%i" -acodec alac  "%o" && mkdir -p /home/doug/tmp/m4a/"%a"\ \("%y"\)\ "%b" && AtomicParsley "%o" -o /home/doug/tmp/m4a/"%a"\ \("%y"\)\ "%b"/"%n"\ -\ "%t".aac --artist "%a" --album "%b" --tracknum "%n" --year "%y" --title "%t"  --genre "%g" && rm "%o"

CDDB INFO

Artist	= Funk Brothers
Album	= Standing In The Shadows Of Motown (Soundtrack)
Year	= 2004
Genre	= Soul
Tracks	= 15 (1 selected)

08 - What Becomes Of The Brokenhearted - Joan Osborne

STATUS

Starting to rip track 8, trial #1 (53 seconds)
Starting to rip track 8, trial #2 (53 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 4815bffb00dfdaa7894670ab6756287f


RIPPING SUMMARY

All chunks were tried to match at least 2 times.
None of the tracks gave any problems

batch rename - at directory prompt where the .aac's are - 
```
 for f in *.aac; do mv "$f" "${f%.aac}.m4a"; done;
```

---

### Post by mc4man on 2010-07-20
shantiq - here's one more for your collection - value probably nil but anyway...
als.mp4

command is set to create access points - that was the only way to play in vlc, mplayer could care less.
Note that most   vlc 1.0.X builds cannot decode - that where I came across this codec while getting vlc 1.0.5+ to decode (have patch I created to allow vlc 1.0.X to support
I believe vlc 1.1.X can decode 

 basic other comm. - the -r1 sets access points - explore the help file if inclined

```
mp4alsRM22rev2  -r1  %i  "%o".mp4
```

forgot where I found the encoder and decoder - shouldn't be hard to locate
> ~$ mp4alsRM22rev2 -h
mp4alsRM22rev1 - MPEG-4 Audio Lossless Coding (ALS), Reference Model Codec
  Version 22 for Linux
  (c) 2003-2008 Tilman Liebchen, TU Berlin / LG Electronics
    E-mail: [email]liebchen@nue.tu-berlin.de[/email]
  Portions by Yuriy A. Reznik, RealNetworks, Inc.
    E-mail: [email]yreznik@real.com[/email]
  Portions by Koichi Sugiura, NTT Advanced Technology corporation
    E-mail: [email]koichi.sugiura@ntt-at.co.jp[/email]
  Portions by Takehiro Moriya, Noboru Harada and Yutaka Kamamoto, NTT
    E-mail: {moriya.takehiro,harada.noboru,kamamoto.yutaka}@lab.ntt.co.jp

Usage: mp4alsRM22rev1 [options] infile [outfile]

  In compression mode, infile must be a PCM file (wav, aif, or raw format)
  or a 32-bit floating point file (normalized, wav format type 3).
  Mono, stereo, and multichannel files with up to 65536 channels and up to
  32-bit resolution are supported at any sampling frequency.
  In decompression mode (-x), infile is the compressed file (.als or .mp4).
  If outfile is not specified, the name of the output file will be generated
  by replacing the extension of the input file (wav <-> als).
  If outfile is '-', the output will be written to stdout. If infile is '-',
  the input will be read from stdin, and outfile has to be specified.

General Options:
  -c  : Check accuracy by decoding the whole file after encoding.
  -d  : Delete input file after completion.
  -h  : Help (this message)
  -v  : Verbose mode (file info, processing time)
  -x  : Extract (all options except -v and -MP4 are ignored)
Encoding Options:
  -7  : Set parameters for optimum compression (except LTP, MCC, RLSLMS)
  -a  : Adaptive prediction order
  -b  : Use BGMC codes for prediction residual (default: use Rice codes)
  -e  : Exclude CRC calculation
  -f# : ACF/MLZ mode: # = 0-7, -f6/-f7 requires ACF gain value
  -g# : Block switching level: 0 = off (default), 5 = maximum
  -i  : Independent stereo coding (turn off joint stereo coding)
  -l  : Check for empty LSBs (e.g. 20-bit files)
  -m# : Rearrange channel configuration (example: -m1,2,4,5,3)
  -n# : Frame length: 0 = auto (default), max = 65536
  -o# : Prediction order (default = 10), max = 1023
  -p  : Use long-term prediction
  -r# : Random access (multiples of 0.1 sec), -1 = each frame, 0 = off (default)
  -s# : Multi-channel correlation (#=1-65536, jointly code every # channels)
        # must be a divisor of number of channels, otherwise -s is ignored
  -t# : Two methods mode (Joint Stereo and Multi-channel correlation)
        # must be a divisor of number of channels
  -u# : Random access info location, 0 = frames (default), 1 = header, 2 = none
  -z# : RLSLMS mode (default = 0: no RLSLMS mode,  1-quick, 2-medium 3-best )
MP4 File Format Support:
  -MP4: Use MP4 file format for compressed file (default if extension is .mp4)
  -OAFI:Force to embed meta box with oafi record
Audio file support:
  -R  : Raw audio file (use -C, -W, -F and -M to specify format)
  -S# : Sample type: 0 = integer (default), 1 = float
  -C# : Number of Channels (default = 2)
  -W# : Word length in bits per sample (default = 16)
  -F# : Sampling frequency in Hz (default = 44100)
  -M  : 'MSByte first' byte order (otherwise 'LSByte first')
  -H# : Header size in bytes (default = 0)
  -T# : Trailer size in bytes (default = 0)
  -I  : Show info only, no (de)compression (add -x for compressed files)






---

### Post by shantiq on 2010-07-20
wow Mc4man never heard of that one :KS will have a look   cheers



[here]("http://www.nue.tu-berlin.de/fileadmin/fg97/Forschung/Projekte/Beendete_Projekte/MPEG4_ALS/mp4alsRM22rev2.zip")

from   [http://wiki.multimedia.cx/index.php?title=MPEG-4_ALS](http://wiki.multimedia.cx/index.php?title=MPEG-4_ALS)


also for EAC

Preparations (necessary only once)



Start the Exact Audio Copy application and select the menu item "EAC > Compression Options".

In the following dialog box, choose the tab "External Compression" and set the compression options according to the following explanations and the screenshot:

Select "Use external program for compression"
Set "Parameter passing scheme" to "User Defined Encoder" (last of the drop-down list)
Set "Use file extension" to ".mp4"
Provide path to ALS encoder (mp4alsRM22rev2.exe or later)
Set "Additional command-line options" to "-v -a -o15 -r-1 %s %d". Other options are possible (type "mp4alsRM22rev2 -h" for a list), but %s and %d always have to be the last two since they stand for source and destination file.
The "Bit rate " and "Quality" options don't do anything. You may set "Bit rate" to "768 kBit/s" to get a rough estimate of the compressed file size to be expected.
Select "Delete WAV" if you want the intermediary wave file to be removed.
Deselect "Use CRC check" and "Add ID3 tag"
Preferably select "Check for external programs return code" in order to get feedback in case of errors.
Click "OK" to save the settings and close the dialog box.


[URL="http://www.nue.tu-berlin.de/menue/forschung/projekte/beendete_projekte/mpeg-4_audio_lossless_coding_als/parameter/en/#253204"]Software that supports MPEG-4 ALS
[/URL]




well it rips fine and plays on VLC and SMplayer

---

### Post by shantiq on 2010-07-24
```

```also  **rip to ape**


install mac (attached)

external 
code is

```
mac  "%i" "%o".ape -c5000
```


you can change speed of compression

```
Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
5000 is slower but higher compression
1000 is faster but lower compression /bigger file

```


example


```
shantiq@shantiq-desktop:~$ rrip_cli 
Scanning disc with cdrdao
Audio-disc found, number of tracks : 10, total playlength : 45:00
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: Prince
Album: Planet Earth
Genre: R&B
Year: 2007

TRACK INFO
1) Planet Earth
2) Guitar
3) Somewhere Here On Earth
4) The One U Wanna C
5) Future Baby Mama
6) Mr. Goodnight
7) All The Midnights In The World
8) Chelsea Rodgers
9) Lion of Judah
10) Resolution

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] 
1
Should all tracks be ripped ? (y/n)  [y] Please answer yes or no

n
Should all tracks be ripped ? (y/n)  [y] Current selection of tracks : 1 2 3 4 5 6 7 8 9 10
Enter 1 for entering the tracknumbers you want to remove.
Enter 2 for entering the tracks you want to keep.
2
Your choice:  [1] 10
Type the numbers of the tracks you want to keep and separate them with a space: Current selection of tracks : 10

Do you want to make any changes? (y/n) :  [n] mac  "%i" "%o" .ape -c5000
/home/shantiq/other/Prince (2007) Planet Earth
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] /home/shantiq/other/Prince (2007) Planet Earth#10
01 - Planet Earth .ape
02 - Guitar .ape
03 - Somewhere Here On Earth .ape
04 - The One U Wanna C .ape
05 - Future Baby Mama .ape
06 - Mr. Goodnight .ape
07 - All The Midnights In The World .ape
08 - Chelsea Rodgers .ape
09 - Lion of Judah .ape
10 - Resolution .ape
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> mac  "%i" "%o" -c5000

CDDB INFO

Artist	= Prince
Album	= Planet Earth
Year	= 2007
Genre	= R&B
Tracks	= 10 (1 selected)

10 - Resolution

ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while

Loading file: /tmp/temp_cdrom.toc
Disc type = CD_DA
Found info of tracknumber 1
Found info of tracknumber 2
Found info of tracknumber 3
Found info of tracknumber 4
Found info of tracknumber 5
Found info of tracknumber 6
Found info of tracknumber 7
Found info of tracknumber 8
Found info of tracknumber 9
Found info of tracknumber 10
Debug info: gaps are now prepended
Startsector	Lengthsector
0	26356
26356	16893
43249	25938
69187	20203
89390	21556
110946	20001
130947	10642
141589	25585
167174	18809
185983	16549
No pregaps, silences or pre-emphasis detected


STATUS

Ripping progress (0 %)
Ripping track 10
Expected filesize for track 10		is 38923292 bytes.
Free disk space is 393864932 MB
Minutes ripping is 0.000398266666666667.
Starting to rip track 10, trial #1cdparanoia [.185983]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track10_1.wav" 2>&1
 (17 seconds)
Minutes ripping is 0.2891112.
Starting to rip track 10, trial #2cdparanoia [.185983]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track10_2.wav" 2>&1
 (17 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 838db5798978d819283b022fdc2b05d3

Ripping progress (100 %)
Encoding progress (0 %)
Adding track 10 (other) to the queue..
command = mac  "/home/shantiq/other/temp_sr0/track10_1.wav" "/home/shantiq/other/Prince (2007) Planet Earth#10/10 - Resolution .ape" -c5000
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Compressing (insane)...
Progress: 100.0% (0.0 seconds remaining, 25.7 seconds total)          
Success...
Encoding progress (100 %)
Removing track 10 (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ 
```

---

### Post by shantiq on 2010-07-24
**For m4a/aac**


install


```
sudo aptitude install faac
```


then external encoder line is (kbps around 290)


```
faac --artist %a --album %b --title %t --genre %g --track %n --year %y -o %o.m4a  -q 500  %i
```


sample

```
shantiq@shantiq-desktop:~$ rrip_cli
Scanning disc with cdrdao
Audio-disc found, number of tracks : 10, total playlength : 45:00
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: Prince
Album: Planet Earth
Genre: R&B
Year: 2007

TRACK INFO
1) Planet Earth
2) Guitar
3) Somewhere Here On Earth
4) The One U Wanna C
5) Future Baby Mama
6) Mr. Goodnight
7) All The Midnights In The World
8) Chelsea Rodgers
9) Lion of Judah
10) Resolution

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

1
Please enter the number of your choice:  [1] 
1
Should all tracks be ripped ? (y/n)  [y] Please answer yes or no

Should all tracks be ripped ? (y/n)  [y] n
Current selection of tracks : 1 2 3 4 5 6 7 8 9 10
Enter 1 for entering the tracknumbers you want to remove.
Enter 2 for entering the tracks you want to keep.
Your choice:  [1] 2
Type the numbers of the tracks you want to keep and separate them with a space: 10
Current selection of tracks : 10
Do you want to make any changes? (y/n) :  [n] n
faac --artist "%a" --album "%b" --title "%t" --genre "%g" --track "%n" --year "%y" -o "%o".m4a  -q 500  "%i"
/home/shantiq/other/Prince (2007) Planet Earth
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 1
/home/shantiq/other/Prince (2007) Planet Earth#1
01 - Planet Earth.m4a
02 - Guitar.m4a
03 - Somewhere Here On Earth.m4a
04 - The One U Wanna C.m4a
05 - Future Baby Mama.m4a
06 - Mr. Goodnight.m4a
07 - All The Midnights In The World.m4a
08 - Chelsea Rodgers.m4a
09 - Lion of Judah.m4a
10 - Resolution.m4a
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> faac --artist "%a" --album "%b" --title "%t" --genre "%g" --track "%n" --year "%y" -o "%o"  -q 500  "%i"

CDDB INFO

Artist	= Prince
Album	= Planet Earth
Year	= 2007
Genre	= R&B
Tracks	= 10 (1 selected)

10 - Resolution

ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while

Debug info: gaps are now prepended
Startsector	Lengthsector
0	26356
26356	16893
43249	25938
69187	20203
89390	21556
110946	20001
130947	10642
141589	25585
167174	18809
185983	16549

STATUS

Ripping progress (0 %)
Ripping track 10
Expected filesize for track 10		is 38923292 bytes.
Free disk space is 391747216 MB
Minutes ripping is 0.000391866666666667.
Starting to rip track 10, trial #1cdparanoia [.185983]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track10_1.wav" 2>&1
 (21 seconds)
Minutes ripping is 0.35477845.
Starting to rip track 10, trial #2cdparanoia [.185983]- -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track10_2.wav" 2>&1
 (17 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 838db5798978d819283b022fdc2b05d3

Ripping progress (100 %)
Encoding progress (0 %)
Adding track 10 (other) to the queue..
command = faac --artist "Prince" --album "Planet Earth" --title "Resolution" --genre "R&B" --track "10" --year "2007" -o "/home/shantiq/other/Prince (2007) Planet Earth#1/10 - Resolution.m4a"  -q 500  "/home/shantiq/other/temp_sr0/track10_1.wav"
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

Quantization quality: 500
Bandwidth: 22050 Hz
Object type: Low Complexity(MPEG-4) + M/S
Container format: MPEG-4 File Format (MP4)
Encoding /home/shantiq/other/temp_sr0/track10_1.wav to /home/shantiq/other/Prince (2007) Planet Earth#1/10 - Resolution.m4a
   frame          | bitrate | elapsed/estim | play/CPU | ETA
 9504/9504  (100%)|  303.1  |   18.9/18.9   |   11.66x | 0.0  

Encoding progress (100 %)
Removing track 10 (other) from the queue..
Inside the finished function
Encoding progress (100 %)

```

---

### Post by shantiq on 2010-07-24
SUMMARY
=======


    &#9679; **[FONT=century gothic]shorten[/FONT]** ```
shorten "%i" "%o".shn && id3v2 %o.shn --artist %a --album %b --song %t --genre %g --track %n --year %y --comment Ripped.with.Rubyripper
```

    &#9679; **[FONT=century gothic]alac[/FONT]**   > ffmpeg  -i %i -codec alac -metadata ARTIST=%a -metadata ALBUM=%b -metadata GENRE=%g -metadata DATE=%y -metadata TRACK=%n -metadata TITLE=%t -metadata COMMENT="Ripped.Rubyripper.By.Yourname" %o.m4a

you can use avconv too [thanx burke]

&#9679; **[FONT=century gothic]opus[/FONT]**               ```
 opusenc --bitrate 128 "%i" "%o".opus && id3v2 "%o".opus --artist "%a" --album "%b" --song "%t" --genre "%g" --track "%n" --year "%y"
```

    &#9679; **[FONT=century gothic]wavpack[/FONT]**                                                > wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"

    &#9679; **[FONT=century gothic]mp3HD[/FONT]**

    > mp3hdEncoder -br 320000 -if "%i" -of "%o".mp3 - -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"

    ALSO IMPORTANT for mp3hdEncoder


    MAke sure you have Lame installed on your synaptic the encoding relies on it for the lossy part and make it executable

    ALSO make sure you go into the terminal
    enter mp3hdEncoder and ACCEPT the agreement


    &#9679; **[FONT=century gothic]tta[/FONT]**```
ttaenc -e "%i" -o "%o".tta && id3v2 %o.tta --artist %a --album %b --song %t --genre %g --track %n --year %y
``` 


    &#9679; **[FONT=century gothic]m4a/aac[/FONT]**


    > neroAacEnc -q 1 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t 

&#9679; **[FONT=century gothic][fdkaac]("https://launchpad.net/~mc3man/+archive/fdkaac-encoder")[/FONT]**

```
MPEG-4 AAC LC (default)
MPEG-4 HE-AAC (SBR)
MPEG-4 HE-AAC v2 (SBR+PS)
MPEG-4 AAC LD
MPEG-4 AAC ELD
MPEG-2 AAC LC
MPEG-2 HE-AAC (SBR)
MPEG-2 HE-AAC v2 (SBR+PS)
```


&#9679; to get HE-AAC v2 [very small size but great sound] use

```
fdkaac -p 29 -b 38000 --title "%t" --artist "%a" --album "%b" --track "%n" --date "%y" --genre "%g" --comment Ripped.with.Rubyripper %i -o %o.m4a
```

&#9679; for a regular LC 320k

```
fdkaac -b 320000 --title "%t" --artist "%a" --album "%b" --track "%n" --date "%y" --genre "%g" --comment Ripped.with.Rubyripper %i -o %o.m4a
```

    &#9679; **[FONT=century gothic]ape [/FONT]**

    with tags id3v2 > mac "%i" "%o".ape -c5000 && id3v2 %o.ape --artist %a --album %b --song %t --genre %g --track %n


    also with tags apetag (attached) see [instructions]("http://http://ubuntuforums.org/showpost.php?p=11077345&postcount=27")


    > mac "%i" "%o".ape -c5000 && apetag -i %o.ape -m overwrite -p trackname=%t -p Artist=%a -p Album=%b -p Year=%y -p Track=%n -p Codec=%f

   &#9679; **[FONT=century gothic]musepack[/FONT]**


    > mpcenc --quality 10.00 --artist "%a" --title "%t" --album "%b" --genre "%g" --year "%y" -if "%i" "%o" .mpc


    &#9679; **[FONT=century gothic][bonk ]("http://http://ubuntuforums.org/attachment.php?attachmentid=165685&d=1281134241")[/FONT]**here is a version of the codec which works (courtesy of Mc4man)


if you want a lossless rip

> bonk encode -l "%i" -o "%o".bonk


[  &#9679; **[FONT=century gothic]OptimFrog[/FONT]**]("http://losslessaudio.org/")

> ofr --encode "%i" --output "%o" .ofr && id3v2 %o --artist %a --album %b --song %t --genre %g --track %n --year %y



==================IMPORTANT====================================

Before you do any of the above you need to move your codec to /usr/bin and make it executable

```
sudo mv nameofcodec /usr/bin
```

and then make it executable

```
cd /usr/bin
```

```
sudo chmod +x nameofcodec
```

---

### Post by mc4man on 2010-07-24
> For m4a/aac

I've always prefered neroAacEnc for m4a - which we use a bit here for an ipod dock we drag to jobs, over faac
The non tagged command is simple , the tagged while encoding is the && ... as with als  - may try with mutagen
(actually use abcde for nero, no minor issue with ext. - have made a abcde-nero version (packaged as a standalone or as a 2nd installed abcde  - command is abcde-nero

Also changed abcde to allow either cdparanoia or the **non debian ver**. of cdda2wav

Blue is adjustable - over 0.75 is a waste
```
neroAacEnc -q 0.[COLOR="Blue"]65[/COLOR] -if %i -of "%o".m4a
```

---

### Post by shantiq on 2010-07-24
```

```mc4man you might like this article  the nero one is highly rated

[http://www.hydrogenaudio.org/forums/index.php?showtopic=36465](http://www.hydrogenaudio.org/forums/index.php?showtopic=36465)




also


```
*************************************************************
*                                                           *
*  Nero AAC Encoder                                         *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Dec 17 2009                          *
*  Package version:    1.5.1.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

Usage:
neroAacEnc [options] -if <input-file> -of <output-file>

Where:
<input-file>  : Path to source file to encode.
                The file must be in Microsoft WAV format and contain PCM data.
                Specify - to encode from stdin.
<output-file> : Path to output file to encode to, in MP4 format.

  ==== Available options: ====

Quality/bitrate control:
-q <number>   : Enables "target quality" mode.
                <number> is a floating-point number in 0...1 range.
-br <number>  : Specifies "target bitrate" mode.
                <number> is target bitrate in bits per second.
-cbr <number> : Specifies "target bitrate (streaming)" mode.
                <number> is target bitrate in bits per second.
                When neither of above quality/bitrate options is used,
                the encoder defaults to equivalent of -q 0.5

Multipass encoding:
-2pass        : Enables two-pass encoding mode.
                Note that two-pass more requires a physical file as input,
                rather than stdin.
-2passperiod  : Overrides two-pass encoding bitrate averaging period,
  <number>    : in milliseconds.
              : Specify zero to use least restrictive value possible (default).

Advanced features / troubleshooting:
-lc           : Forces use of LC AAC profile (HE features disabled)
-he           : Forces use of HE AAC profile (HEv2 features disabled)
-hev2         : Forces use of HEv2 AAC profile
                Note that the above switches (-lc, -he, -hev2) should not be
                used; optimal AAC profile is automatically determined from
                quality/bitrate settings when no override is specified.
-ignorelength : Ignores length signaled by WAV headers of input file.
                Useful for certain frontends using stdin.
```

---

### Post by shantiq on 2010-07-24
**ogg**


oggenc is the codec


```
oggenc  -q 10 "%i" -o "%o" .ogg
```

10 is really high about 499 kbps about a third of a wav i am happy with that but 0.75 is probably
a good choice

options in terminal

```
oggenc -h
```   

```
 -q, --quality        Specify quality, between -1 (very low) and 10 (very
                      high), instead of specifying a particular bitrate.
                      This is the normal mode of operation.
                      Fractional qualities (e.g. 2.75) are permitted
                      The default quality level is 3.

```

---

### Post by mc4man on 2010-07-27
shantiq - 
decided to revisit using neroAacTag which wasn't working so good here a year or two ago - works perfectly and much more straightforward than atomicparsley

Ex. comm.
```
neroAacEnc -q 0.65 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t

```

(I'm using a ~/bin for the nero binaries, which oddly I also don't remember that working previously for rr - thought they had to be in /usr/bin or /usr/local/bin - apparently not

Edit:
gotta go out  but possibly neroAacTag can be used for alac also

---

### Post by shantiq on 2010-07-27
sorry mc4man a bit confused where can I find neroAacTag

is it separate from the neroAacEnc codec ?

```
Ripping progress (100 %)
Encoding progress (0 %)
Adding track 1 (other) to the queue..
command = neroAacEnc -q 0.65 -if "/home/shantiq/other/temp_sr0/track1_1.wav" -of "/home/shantiq/other/ATC (2000) Planet Pop/01 - Introducing ATC.m4a" && neroAacTag "/home/shantiq/other/ATC (2000) Planet Pop/01 - Introducing ATC.m4a" -meta:artist="ATC" -meta:album="Planet Pop" -meta:genre="Pop" -meta:year="2000" -meta:track="01" -meta:title="Introducing ATC"
*************************************************************
*                                                           *
*  Nero AAC Encoder                                         *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Feb 18 2010                          *
*  Package version:    1.5.4.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

Processed 40 seconds...
sh: neroAacTag: not found
WARNING: Encoding to other exited with an error with track 1!
Encoding progress (100 %)
Removing track 1 (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ 

```

---

### Post by ron999 on 2010-07-27
Hi shantiq
Download the package NeroAACCodec-1.5.1.zip from here:-[http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php]("http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php")
Unzip it and look in the linux folder inside the NeroAACCodec-1.5.1 folder.
There's three files in there:- neroAacDec, neroAacEnc and neroAacTag.
Make neroAacTag executable and put it in usr/local/bin folder.
Then test it using [B]neroAacTag -help
[/B]
> ron@ubuntu:~$ neroAacTag -help
*************************************************************
*                                                           *
*  Nero MPEG-4 Audio Tagger                                 *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Dec 17 2009                          *
*  Package version:    1.5.1.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************


---

### Post by shantiq on 2010-07-27
thank you Ron

when i installed the encoder the other day i only used the Enc 

disregarded the other 2 cheers


I put it  in /usr/bin  which it seems to accept too


all 3 codecs attached


```
Encoding progress (0 %)
Adding track 2 (other) to the queue..
command = neroAacEnc -q 0.65 -if "/home/shantiq/other/temp_sr0/track2_1.wav" -of "/home/shantiq/other/ATC (2000) Planet Pop#2/02 - Around The World (La La La La La).m4a" && neroAacTag "/home/shantiq/other/ATC (2000) Planet Pop#2/02 - Around The World (La La La La La).m4a" -meta:artist="ATC" -meta:album="Planet Pop" -meta:genre="Pop" -meta:year="2000" -meta:track="02" -meta:title="Around The World (La La La La La)"
*************************************************************
*                                                           *
*  Nero AAC Encoder                                         *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Feb 18 2010                          *
*  Package version:    1.5.4.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

Processed 214 seconds...
*************************************************************
*                                                           *
*  Nero MPEG-4 Audio Tagger                                 *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Dec 17 2009                          *
*  Package version:    1.5.1.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

Processing file: "/home/shantiq/other/ATC (2000) Planet Pop#2/02 - Around The World (La La La La La).m4a"
Updating MP4 file...
File updated successfully.
Encoding progress (100 %)
Removing track 2 (other) from the queue..
Inside the finished function
Encoding progress (100 %)

```

---

### Post by shantiq on 2010-07-27
and yes mc4man you are right again works with alac beautifully:KS:KS


```
ffmpeg  -i %i -acodec alac  "%o".m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track="%n" -meta:title="%t"
```




```
Codec(s) used:
-other	-> ffmpeg  -i "%i" -acodec alac  "%o" && neroAacTag "%o" -meta:artist="%a" -meta:album="%b" -meta:genre="%g" -meta:year="%y" -meta:track="%n" -meta:title="%t"

CDDB INFO

Artist	= ATC
Album	= Planet Pop
Year	= 2000
Genre	= Pop
Tracks	= 18 (1 selected)

03 - My heart beats like a drum (dum dum dum )

ADVANCED TOC ANALYSIS (with cdrdao)
...please be patient, this may take a while


Ripping progress (0 %)
Ripping track 3
Expected filesize for track 3		is 39720620 bytes.
Free disk space is 389192440 MB
Minutes ripping is 0.00034975.
Starting to rip track 3, trial #1cdparanoia [.19188]-[.16887] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track3_1.wav" 2>&1
 (29 seconds)
Minutes ripping is 0.498658066666667.
Starting to rip track 3, trial #2cdparanoia [.19188]-[.16887] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track3_2.wav" 2>&1
 (29 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 8a2c58446b66bdce6a657e173ad14382

Ripping progress (100 %)
Encoding progress (0 %)
Adding track 3 (other) to the queue..
command = ffmpeg  -i "/home/shantiq/other/temp_sr0/track3_1.wav" -acodec alac  "/home/shantiq/other/ATC (2000) Planet Pop#3/03 - My heart beats like a drum (dum dum dum ).m4a" && neroAacTag "/home/shantiq/other/ATC (2000) Planet Pop#3/03 - My heart beats like a drum (dum dum dum ).m4a" -meta:artist="ATC" -meta:album="Planet Pop" -meta:genre="Pop" -meta:year="2000" -meta:track="03" -meta:title="My heart beats like a drum (dum dum dum )"
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, wav, from '/home/shantiq/other/temp_sr0/track3_1.wav':
  Duration: 00:03:45.17, bitrate: 1411 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Output #0, ipod, to '/home/shantiq/other/ATC (2000) Planet Pop#3/03 - My heart beats like a drum (dum dum dum ).m4a':
    Stream #0.0: Audio: alac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   30161kB time=225.23 bitrate=1097.0kbits/s    
video:0kB audio:30142kB global headers:0kB muxing overhead 0.064947%
*************************************************************
*                                                           *
*  Nero MPEG-4 Audio Tagger                                 *
*  Copyright 2009 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Dec 17 2009                          *
*  Package version:    1.5.1.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

Processing file: "/home/shantiq/other/ATC (2000) Planet Pop#3/03 - My heart beats like a drum (dum dum dum ).m4a"
Updating MP4 file...
File updated successfully.
Encoding progress (100 %)
Removing track 3 (other) from the queue..
Inside the finished function
Encoding progress (100 %)

```

---

### Post by mc4man on 2010-07-27
Works fine on alac also - 
```
ffmpeg  -i %i -acodec alac  "%o".m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t
```


(except possible some rare commands - like that atomicparsley one, you shouldn't need to use "" in commands - rr will add them, doesn'y really matter either way, a bit cleaner looking without//

I see we were posting at same time...

---

### Post by shantiq on 2010-07-28
those alac tracks sound so good mind you they play at around 1300 kbps so almost as good as a wave

thanx for the info on ""

---

### Post by shantiq on 2010-07-28
so reading [this article on lossy]("http://www.hydrogenaudio.org/forums/index.php?showtopic=36465") it says


> Last summer I performed a blind listening comparison between three different audio formats, all set for ~175 kbps encodings. The purpose of the test was to investigate about encoding quality with classical music (and only classical) and to see which format would be the most efficient (i.e. the closest to transparency at lowest bitrate possible) for this kind of music. As jumping-off place for bitrate I took MPC &#8211;standard preset which was indisputably recognized as the best encoding solution outputing at 175...190 kbps on average. And indeed, the test ended on [COLOR="Red"]musepack superiority[/COLOR]. MPC was even superior to Vorbis and MP3 at presets presenting higher bitrate (~195 kbps for LAME, ~185 for Vorbis against ~175 for musepack). Consequently, MPC encodings appeared to sound better and to be smaller at the same time. Amazed by the existent gap between all contenders I conclude my specific test with these words: &#8220;I didn&#8217;t think that MPC &#8211;standard was so in advance&#8221;.



so let us try musepack

mppenc   is the encoder

```
mppenc  -if "%i" "%o" .mpc
```

gives  you

```
Encoding progress (0 %)
Adding track 4 (other) to the queue..
command = mppenc  -if "/home/shantiq/other/temp_sr0/track4_1.wav" "/home/shantiq/other/Ultra Nate (2001) Stranger Than Fiction#3/04 - Desire .mpc"
MPC Encoder  1.16  --Stable--   (C) 1999-2006 Buschmann/Klemm/Piecha/MDT
     
 encoding file '/home/shantiq/other/temp_sr0/track4_1.wav'
       to file '/home/shantiq/other/Ultra Nate (2001) Stranger Than Fiction#3/04 - Desire .mpc'

 SV 7.0 + XLevel coding, Profile 'Standard'

    %|avg.bitrate| speed|play time (proc/tot)| CPU time (proc/tot)| ETA
100.0  166.2 kbps 23.29x     4:13.4    4:13.4     0:10.8    0:10.8           
Encoding progress (100 %)
Removing track 4 (other) from the queue..
Inside the finished function
Encoding progress (100 %)

```





```
OPTIONS
       --quality 0.00
              below telephone, poor quality (~ 20 kbps)

       --quality 1.00
              below telephone, poor quality (~ 30 kbps)

       --quality 2.00 --telephone
              telephone, low quality (~ 60 kbps)

       --quality 3.00 --thumb
              thumb, low/medium quality (~ 90 kbps)

       --quality 4.00 --radio
              radio, medium quality (~ 130 kbps)

       --quality 5.00 --standard --normal
              normal (default), high quality (~ 180 kbps)

       --quality 6.00 --extreme --xtreme
              extreme, excellent quality (~ 210 kbps)

       --quality 7.00 --insane
              insane, excellent quality (~ 240 kbps)

       --quality 8.00 --braindead
              braindead, excellent quality (~ 270 kbps)

       --quality 9.00
              above braindead, excellent quality (~ 300 kbps)

       --quality 10.00
              above braindead, excellent quality (~ 350 kbps)

       In  addition,  quality  scale is effective centesimally (i.e. --quality
       4.25).

```

example   


```
mppenc --quality 8.00 -if "%i" "%o" .mpc
```


or say 

```
mppenc --xtreme -if "%i" "%o".mpc
```


and with tagging


```
mppenc --quality 10.00  --artist "%a" --title "%t" --album "%b" --genre "%g" --year "%y" -if "%i" "%o" .mpc
```








```
Encoding progress (0 %)
Adding track 7 (other) to the queue..
command = mppenc  --quality 10.00 -if "/home/shantiq/other/temp_sr0/track7_1.wav" "/home/shantiq/other/Ultra Nate (2001) Stranger Than Fiction#6/07 - Twisted .mpc"
MPC Encoder  1.16  --Stable--   (C) 1999-2006 Buschmann/Klemm/Piecha/MDT
     
 encoding file '/home/shantiq/other/temp_sr0/track7_1.wav'
       to file '/home/shantiq/other/Ultra Nate (2001) Stranger Than Fiction#6/07 - Twisted .mpc'

 SV 7.0 + XLevel coding, Profile 'above BrainDead'

    %|avg.bitrate| speed|play time (proc/tot)| CPU time (proc/tot)| ETA
100.0  336.9 kbps 22.39x     6:41.8    6:41.8     0:17.9    0:17.9           
Encoding progress (100 %)
Removing track 7 (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ 

```


ps plays in most players   tried  deadbeef xmms (plugin attached) audacious qmmp

---

### Post by shantiq on 2010-08-07
ok one more this one is interesting to me since it only seems to play on xmms with the attached plugin please say if you know of other players

i could not find the codec at first then mc4man attached it on this site ( i re-attach it here)

so the code if you want it lossless


```
bonk encode -l "%i" -o "%o".bonk
```

---

### Post by shantiq on 2010-09-09
> **shantiq said:**
> wow Mc4man never heard of that one :KS will have a look   cheers



[here]("http://www.nue.tu-berlin.de/fileadmin/fg97/Forschung/Projekte/Beendete_Projekte/MPEG4_ALS/mp4alsRM22rev2.zip")

from   [http://wiki.multimedia.cx/index.php?title=MPEG-4_ALS](http://wiki.multimedia.cx/index.php?title=MPEG-4_ALS)


also for EAC

```
Preparations (necessary only once)



Start the Exact Audio Copy application and select the menu item "EAC > Compression Options".

In the following dialog box, choose the tab "External Compression" and set the compression options according to the following explanations and the screenshot:

Select "Use external program for compression"
Set "Parameter passing scheme" to "User Defined Encoder" (last of the drop-down list)
Set "Use file extension" to ".mp4"
Provide path to ALS encoder (mp4alsRM22rev2.exe or later)
Set "Additional command-line options" to "-v -a -o15 -r-1 %s %d". Other options are possible (type "mp4alsRM22rev2 -h" for a list), but %s and %d always have to be the last two since they stand for source and destination file.
The "Bit rate " and "Quality" options don't do anything. You may set "Bit rate" to "768 kBit/s" to get a rough estimate of the compressed file size to be expected.
Select "Delete WAV" if you want the intermediary wave file to be removed.
Deselect "Use CRC check" and "Add ID3 tag"
Preferably select "Check for external programs return code" in order to get feedback in case of errors.
Click "OK" to save the settings and close the dialog box.
```


[URL="http://www.nue.tu-berlin.de/menue/forschung/projekte/beendete_projekte/mpeg-4_audio_lossless_coding_als/parameter/en/#253204"]Software that supports MPEG-4 ALS
[/URL]




well it rips fine and plays on VLC and SMplayer



well guess what when i tried it back in july it would not work but now in VLC and SM player no problem whatsoever so it is one more lossless codec one can enjoy and rip with rubyripper

---

### Post by shantiq on 2010-12-20
made a video to show how to do all of the above    the entire process of using rubyripper for lossless ripping

[**_here_**]("http://www.youtube.com/watch?v=TBsnL-ONgJg")

---

### Post by shantiq on 2011-01-14
trying to see if it is possible to rip to [tak ]("http://thbeck.de/Tak/Tak.html")   which only exists as an exe


i have made    wine and Takc.exe  executable    and cobbled this for the "other" external encoder line

```
wine Takc -e -pMax %s %d .tak
```

but then i get this from the commandline when running rrip_cli

i do not particularly understand what it means

do any of you ?   are there reasons why it would theoretically be impossible to run an exe through wine to encode or is just something much simpler


Thanx for all insights  

```
1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 
/home/shantiq/other/Ashra (1989) Walkin' The Desert#7
/usr/usr/lib/ruby/1.8/rr_lib.rb:1487:in `findExtensionOther': undefined method `[]' for nil:NilClass (NoMethodError)
	from /usr/usr/lib/ruby/1.8/rr_lib.rb:1478:in `attemptDirCreation'
	from /usr/usr/lib/ruby/1.8/rr_lib.rb:1677:in `postfixDir'
	from /usr/usr/lib/ruby/1.8/rr_lib.rb:2603:in `postfixDir'
	from /usr/bin/rrip_cli:427:in `dir_exists'
	from /usr/bin/rrip_cli:447:in `update'
	from /usr/bin/rrip_cli:414:in `prepareRip'
	from /usr/bin/rrip_cli:331:in `showFreedbOptions'
	from /usr/bin/rrip_cli:305:in `showFreedb'
	from /usr/bin/rrip_cli:265:in `handleFreedb'
	from /usr/bin/rrip_cli:244:in `get_cd_info'
	from /usr/bin/rrip_cli:47:in `initialize'
	from /usr/bin/rrip_cli:486:in `new'
	from /usr/bin/rrip_cli:486

```

---

### Post by shantiq on 2012-05-11
Yet one more lossless for the [collection:KS]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26")


[**=> OptimFrog**]("http://losslessaudio.org/")




> ofr  --encode "%i"  --output  "%o" .ofr && id3v2 %o   --artist %a --album %b --song %t --genre %g --track %n --year %y



Probably best place to play those file is Foobar 1.1 under wine with this [**plugin**]("http://www.losslessaudio.org/Downloads/foo_input_ofr_130.zip")


also added here below   [put both dll in Foobar components folder]


can also be played in xmms 32-bit as there is a plugin online   none for 64-bit as yet



[ATTACH]217723[/ATTACH]

---

### Post by shantiq on 2012-09-13
to add to the list of code for [**other codecs **]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26")there is also HE-AAC which allows you to have a very small file of a fairly decent compared sound quality for its size

one can use [**aacplusenc**]("http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc")  or neroAacEnc for that task or even libaacplus through ffmpeg

those are the "other" lines


```
aacplusenc "%i"  "%o" .aac 64000 s
```   or even 

```
aacplusenc "%i"  "%o" .aac 72000 s
```

NB: no tagging with aacplusenc




> neroAacEnc **-hev2** -q 1 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t

tagging here   you change -q 1  for -q 0.5   up to you


 
>  
ffmpeg -i %i -c:a libaacplus -b:a 64k %o.m4a && AtomicParsley %o.m4a -a %a -b %b -g %g -y %y -k %n --title %t -W

Atomic Parsley required for this last one.  It is in repo.   Also you will need to add libaacplus to your ffmpeg   see [**here **]("http://ubuntuforums.org/showpost.php?p=12230041&postcount=1")for details




**PS**   to navigate easy to make those codec changes and bypassing the [at times unreliable] GUI


use this 


> mousepad ./config/rubyripper/settings   or if you do not use mousepad   > gedit ./config/rubyripper/settings

having first made sure the file will, open

> sudo chown yourname ./config/rubyripper/settings



find the line "othersettings" and change

---

### Post by mc4man on 2012-09-13
> **shantiq said:**
> 
PS to navigate easy to make those codec changes and bypassing the [at times unreliable] GUI
use this
> 
cd .config/rubyripper && [COLOR="Blue"]sudo[/COLOR] mousepad settings

or if you do not use mousepad
[QUOTE]
cd .config/rubyripper && [COLOR="Blue"]sudo[/COLOR] gedit settings


find the line "other" and change [/QUOTE]
probably should refrain from using sudo to edit user config files, not needed, you should own them. (or you used to..

---

### Post by shantiq on 2012-09-13
Hi mc4   you mean do this this first


```
sudo chown yourname settings
```   then

```
cd .config/rubyripper && mousepad settings
```



is a better way ?

---

### Post by mc4man on 2012-09-14
basically, take back ownership or create new settings file(s). then if opening from cli just use for ex.

```
mousepad .config/rubyripper/settings

```

(if your terminal was at something other than default prompt then a simple 
cd will return - 

cd
mousepad .config/rubyripper/settings

(you could also look at disown so you can close the terminal

mousepad .config/rubyripper/settings & disown

Myself for stuff like this I do often just use Alt+F2, enter simple commands,  then they are there in the history & just click on - 

Alt+F2
mousepad .config/rubyripper/settings

---

### Post by shantiq on 2012-09-14
[FONT="Century Gothic"]good tip thank you:KS:KS


had completely forgotten the existence of alt+ F2  

of course on the last few versions it is not there.  has to be **[brought back]("http://joesteiger.com/2011/11/06/enable-alt-f2-keyboard-shortcut-ubuntu-11-10/")**


i do not know about others but RR without GUI is usually way smoother[/FONT]

---

### Post by shantiq on 2013-01-21
In earlier [**post**]("http://ubuntuforums.org/showthread.php?p=9630448#post9630448") i had not always shown how to rip **with** tags trying to correct all this now so rips are fully tagged




&#9679;_Command Line for ogg with VorbisComments tags:_


> oggenc  -q 9 -t "%t" -d "%y" -a "%a" -l "%b" -G "%g" -N "%n" -c "%c"  "%i" -o "%o" .ogg

[actually looking again no need for ogg in the Other as it is one of the 3 already available; but i shall leave it here as reference]


&#9679;_Command Line for tta with id3v2 tags_



> ttaenc -e  "%i" -o "%o".tta   && id3v2 %o.tta --artist %a --album %b --song %t --genre %g --track %n  --year %y



[FONT=Century Gothic]

&#9679; _[Command Line for **opus** [a recent lossy codec]]("http://opus-codec.org/")_


> opusenc --bitrate 128   "%i"  "%o".opus   && id3v2 "%o".opus --artist "%a" --album "%b" --song "%t" --genre "%g" --track "%n"  --year "%y"


_&#9679; shorten also can be tagged with id3_
[/FONT][FONT=Century Gothic]

> [/FONT]shorten "%i" "%o".shn && id3v2 %o.shn --artist %a --album %b --song %t --genre %g --track %n --year %y  --comment Ripped.with.Rubyripper[FONT=Century Gothic]

also keeping all info on [**Hydrogenaudio**]("http://www.hydrogenaudio.org/forums/index.php?showtopic=99023")


[/FONT]

---

### Post by shantiq on 2013-04-15
[SIZE=2][FONT=arial]just tested it all in 13.04 and all good it seems


installed RR this way using [guide]("http://pkgs.org/ubuntu-12.04/getdeb-apps-i386/rubyripper_0.6.2-1~getdeb1_all.deb.html")


1.    ```
sudo apt-get install cd-discid
```  then

**2. **```
[COLOR=#000000]wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -[/COLOR]
```

3. ```
sudo gedit [COLOR=#000000]/etc/apt/sources.list[/COLOR]
```[COLOR=#000000]   and add this line and save   [/COLOR]```
[COLOR=#000000]deb http://archive.getdeb.net/ubuntu/ precise-getdeb apps[/COLOR]
```

4. ```
[COLOR=#000000]sudo apt-get update[/COLOR]
```

5. ```
[COLOR=#000000]sudo apt-get install rubyripper[/COLOR]
```[/FONT][/SIZE]

---

### Post by shantiq on 2013-08-14
ok so there is another [brilliant encoder]("https://launchpad.net/~mc3man/+archive/fdkaac-encoder")  [Thank you Doug ..  Mc4man] to allow one to obtain all those formats


>  MPEG-4 AAC LC (default)
 MPEG-4 HE-AAC (SBR)
 MPEG-4 HE-AAC v2 (SBR+PS)
 MPEG-4 AAC LD
 MPEG-4 AAC ELD
 MPEG-2 AAC LC
 MPEG-2 HE-AAC (SBR)
 MPEG-2 HE-AAC v2 (SBR+PS)


 &#9679;  to get HE-AAC v2  [very small size but great sound] use

> fdkaac -p 29 -b 38000   --title "%t" --artist "%a" --album "%b" --track "%n" --date "%y" --genre "%g" --comment Ripped.with.Rubyripper %i  -o %o.m4a

 &#9679;  for a regular LC   320k

> fdkaac  -b 320000   --title "%t" --artist "%a" --album "%b" --track "%n" --date "%y" --genre "%g" --comment Ripped.with.Rubyripper %i  -o %o.m4a



running fdkaac in terminal gives you further settings


```
fdkaac
fdkaac 0.2.0
Usage: fdkaac [options] input_file
Options:
 -h, --help                    Print this help message
 -p, --profile <n>             Profile (audio object type)
                                 2: MPEG-4 AAC LC (default)
                                 5: MPEG-4 HE-AAC (SBR)
                                29: MPEG-4 HE-AAC v2 (SBR+PS)
                                23: MPEG-4 AAC LD
                                39: MPEG-4 AAC ELD
                               129: MPEG-2 AAC LC
                               132: MPEG-2 HE-AAC (SBR)
                               156: MPEG-2 HE-AAC v2 (SBR+PS)
 -b, --bitrate <n>             Bitrate in bits per seconds (for CBR)
 -m, --bitrate-mode <n>        Bitrate configuration
                                 0: CBR (default)
                                 1-5: VBR
                               (VBR mode is not officially supported, and
                                works only on a certain combination of
                                parameter settings, sample rate, and
                                channel configuration)
 -w, --bandwidth <n>           Frequency bandwidth in Hz (AAC LC only)
 -a, --afterburner <n>         Afterburner
                                 0: Off
                                 1: On(default)
 -L, --lowdelay-sbr            Enable ELD-SBR (AAC ELD only)
 -s, --sbr-signaling <n>       SBR signaling mode
                                 0: Implicit, backward compatible(default)
                                 1: Explicit SBR and implicit PS
                                 2: Explicit hierarchical signaling
 -f, --transport-format <n>    Transport format
                                 0: RAW (default, muxed into M4A)
                                 1: ADIF
                                 2: ADTS
                                 6: LATM MCP=1
                                 7: LATM MCP=0
                                10: LOAS/LATM (LATM within LOAS)
 -C, --adts-crc-check          Add CRC protection on ADTS header
 -h, --header-period <n>       StreamMuxConfig/PCE repetition period in
                               transport layer


 -o <filename>                 Output filename
 -G, --gapless-mode <n>        Encoder delay signaling for gapless playback
                                 0: iTunSMPB (default)
                                 1: ISO standard (edts + sgpd)
                                 2: Both
 --ignorelength                Ignore length of WAV header
 -S, --silent                  Don't print progress messages


Options for raw (headerless) input:
 -R, --raw                     Treat input as raw (by default WAV is
                               assumed)
 --raw-channels <n>            Number of channels (default: 2)
 --raw-rate     <n>            Sample rate (default: 44100)
 --raw-format   <spec>         Sample format, default is "S16L".
                               Spec is as follows:
                                1st char: S(igned)|U(nsigned)|F(loat)
                                2nd part: bits per channel
                                Last char: L(ittle)|B(ig)
                               Last char can be omitted, in which case L is
                               assumed. Spec is case insensitive, therefore
                               "u16b" is same as "U16B".


Tagging options:
 --title <string>
 --artist <string>
 --album <string>
 --genre <string>
 --date <string>
 --composer <string>
 --grouping <string>
 --comment <string>
 --album-artist <string>
 --track <number[/total]>
 --disk <number[/total]>
 --tempo <n>
 --tag <fcc>:<value>          Set iTunes predefined tag with four char code.
 --tag-from-file <fcc>:<filename>
                              Same as above, but value is read from file.
 --long-tag <name>:<value>    Set arbitrary tag as iTunes custom metadata.
 --tag-from-json <filename[?dot_notation]>
                              Read tags from JSON. By default, tags are
                              assumed to be direct children of the root
                              object(dictionary).
                              Optionally, position of the dictionary
                              that contains tags can be specified with
                              dotted notation.
                              Example:
                                --tag-from-json /path/to/json?format.tags



```

---

### Post by mc4man on 2013-08-15
The latest RR is avail. to use though it isn't/can't be installed per se. 
(can be discussed at some point if needed
It has a newer way of adding codecs & has fdkaac ('fdkaac-encoder')  support built-in as in screen. (called "Faunhofer AAC", default settings

0.7 does have a current issue with flac-1.3, 1.2 is fine. 
There is a workaround of passing an -s option to flac that allows encoding, it can be done in several ways. The downside is RR will close right after the R&E without deleting the tmp wav files. Hopefully the maintainer will figure a way to fix.

Slight OT edit.
If you are using 13.04 & unity there is a man page scope that's a better way to read man pages (really useful with ffmpeg & mplayer)
Example in screen on fdkaac one.
You can also set bookmarks in the man help scope for individual pages (in it's menu
(if on 12.04 I backported the man scope, in a ppa on request

---

### Post by shantiq on 2013-08-15
nice one Mc   did not know it was even still maintained    ...    great news   ...   there is life in the old beast:KS    also makes it the first ripper which does opus as default


to [get it]("https://code.google.com/p/rubyripper/wiki/Git") use

```
git clone https://code.google.com/p/rubyripper/
```    then cd to rubyripper folder

and enter :

```
./bin/rubyripper_cli
```

or if you are happier tinkering with gui   ```
./bin/rubyripper_gtk2
```

**you may need thes**e if you have not got them on your system ```
sudo apt-get install cd-discid ruby-gettext 
```

great choice of codecs in 0.7

[IMG]http://s20.postimg.org/4p11zjs4d/codecs_rubyripper_0_7_0.png[/IMG]



======

for HE-AAC v2   ```
-p 29 -b 38
```

Also if you untick create cuesheet in TOC analysis the process is much quicker (unless you want a cuesheet of course)



Beautiful!


```
./rubyripper_cliRubyripper version 0.7.0a1


DEBUG: cdparanoia -d /dev/sr1 -vQ
DEBUG: cd-discid /dev/sr1


AUDIO DISC FOUND
Number of tracks: 16
Total playtime: 74:35


DISC INFO
Artist: Boulez
Album: Boulez at 70
Genre: Classical
Year: 1995
Extra disc info: 
Marked as various disc? [ ]


TRACK INFO
1. Fireworks / Stravinksy
2. Pierre Boulez and Stephen Plaistow
3. Nocturnes - Nuages / Debussy
4. Boulez and Plaistow
5. Symphony No 6 - Allegro ma non troppo / Mahler
6. Boulez and Plaistow
7. Vier Lieder, Op 13 / Webern
8. Boulez and Plaistow
9. Orchestral Pieces, Op 12 - Scherzo / Bartok
10. Boulez and Plaistow
11. Chronochromie - Antistrophe I / Messiaen
12. Boulez and Plaistow
13. Violin Concerto - Praeludium / Liegeti
14. Boulez and Plaistow
15. Une barque sur l'ocean / Ravel
16. Boulez and Plaistow


* RUBYRIPPER MAIN MENU *


 1) Change preferences
 2) Scan drive for audio disc
 3) Change metadata
 4) Select the tracks to rip (default = all)
 5) Rip the disc!
99) Exit rubyripper...


Please type the number of your choice [99] : 5
DEBUG: trackselection = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16]
The output directory already exists. What would you like to do?


1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc


Please enter the number of your choice:  [1] : 2
DEBUG: date
DEBUG: cdparanoia --version
Rubyripper version 0.7.0a1
Website: http://code.google.com/p/rubyripper


Rubyripper extraction logfile from:
["Thu Sep  4 11:26:45 BST 2014\r\n"]


Boulez / Boulez at 70


Used drive     : TSSTcorp BDDVDW SE-506BB TS00   Device: /dev/sr1


Used ripper    : cdparanoia III release 10.2 (September 11, 2008)
Selected options : 


Matches required for all chunks       : 2
Matches required for erroneous chunks : 3


Read offset correction                      : 6
Overread into Lead-In and Lead-Out          : No
Fill up missing offset samples with silence : Yes
Null samples used in CRC calculations       : Yes


TOC of the extracted CD


     Track |   Start  |  Length  | Start sector | End sector 
    ---------------------------------------------------------
        1  | 00:00:00 | 03:49:35 |         0    |    17209   
        2  | 03:49:35 | 10:38:05 |     17210    |    65064   
        3  | 14:27:40 | 06:15:45 |     65065    |    93234   
        4  | 20:43:10 | 03:55:20 |     93235    |   110879   
        5  | 24:38:30 | 09:24:25 |    110880    |   153204   
        6  | 34:02:55 | 02:22:67 |    153205    |   163921   
        7  | 36:25:47 | 07:03:00 |    163922    |   195646   
        8  | 43:28:47 | 02:31:65 |    195647    |   207036   
        9  | 46:00:37 | 06:10:25 |    207037    |   234811   
       10  | 52:10:62 | 01:49:73 |    234812    |   243059   
       11  | 54:00:60 | 02:52:05 |    243060    |   255964   
       12  | 56:52:65 | 01:43:70 |    255965    |   263759   
       13  | 58:36:60 | 04:08:70 |    263760    |   282429   
       14  | 62:45:55 | 02:48:10 |    282430    |   295039   
       15  | 65:33:65 | 08:01:20 |    295040    |   331134   
       16  | 73:35:10 | 01:00:35 |    331135    |   335669   


Ripping progress (0 %)
DEBUG: Ripping track 1
DEBUG: Expected filesize for track 1 is 40477964 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: Free disk space is 152102008 MB
DEBUG: Minutes ripping is 0.0019010470166666666.
Track  1


     File name /home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/01 - Fireworks  Stravinksy.m4a


DEBUG: cdparanoia [.0]-[.17209] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_1_1.wav"
     Trial 1: 62 seconds (3.66x)
DEBUG: Minutes ripping is 1.0469342796999999.
DEBUG: cdparanoia [.0]-[.17209] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_1_2.wav"
     Trial 2: 48 seconds (4.69x)
DEBUG: Start of hashes algorithm 2014-09-04 11:28:37 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:28:39 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_1_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:28:41 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:28:42 +0100.
     All chunks matched!


     Peak level 100.0 %
     Trial 1 (Copy) CRC BCAF78DF
     Trial 2 (Test) CRC BCAF78DF
     Copy OK


     Copy MD5: 83fdfed1dd5f96f859e7132828b55c91


Ripping progress (5.13 %)
Encoding progress (0 %)
DEBUG: Adding track 1 (fraunhofer) to the queue..
DEBUG: Ripping track 2
DEBUG: Expected filesize for track 2 is 112555004 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/01 - Fireworks  Stravinksy.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Fireworks / Stravinksy" --track 1 "/home/shantiq/fraunhofer/temp_sr1/track_1_1.wav"
DEBUG: Free disk space is 152061968 MB
DEBUG: Minutes ripping is 1.9599919540666666.
Track  2


     File name /home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/02 - Pierre Boulez and Stephen Plaistow.m4a


DEBUG: cdparanoia [.17210]-[.47854] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_2_1.wav"
Encoding progress (5.13 %)
DEBUG: Removing track 1 (fraunhofer) from the queue..
     Trial 1: 131 seconds (4.85x)
DEBUG: Minutes ripping is 4.151043218716667.
DEBUG: cdparanoia [.17210]-[.47854] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_2_2.wav"
     Trial 2: 145 seconds (4.38x)
DEBUG: Start of hashes algorithm 2014-09-04 11:33:20 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:33:23 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_2_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:33:28 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:33:30 +0100.
     All chunks matched!


     Peak level 88.2 %
     Trial 1 (Copy) CRC EB053539
     Trial 2 (Test) CRC EB053539
     Copy OK


     Copy MD5: 66b0e4be9ba72b7694d6b948144ed32a


Ripping progress (19.4 %)
DEBUG: Adding track 2 (fraunhofer) to the queue..
DEBUG: Ripping track 3
DEBUG: Expected filesize for track 3 is 66255884 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/02 - Pierre Boulez and Stephen Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Pierre Boulez and Stephen Plaistow" --track 2 "/home/shantiq/fraunhofer/temp_sr1/track_2_1.wav"
DEBUG: Free disk space is 151988868 MB
DEBUG: Minutes ripping is 6.765299336616667.
Track  3




DEBUG: cdparanoia [.65065]-[.28169] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_3_1.wav"
Encoding progress (19.4 %)
DEBUG: Removing track 2 (fraunhofer) from the queue..
     Trial 1: 74 seconds (5.03x)
DEBUG: Minutes ripping is 8.0098837413.
DEBUG: cdparanoia [.65065]-[.28169] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_3_2.wav"
     Trial 2: 59 seconds (6.36x)
DEBUG: Start of hashes algorithm 2014-09-04 11:35:45 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:35:47 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_3_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:35:49 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:35:51 +0100.
     All chunks matched!


     Peak level 87.1 %
     Trial 1 (Copy) CRC 9A62C3D1
     Trial 2 (Test) CRC 9A62C3D1
     Copy OK


     Copy MD5: 32585397355fad86264c5f3060518ec2


Ripping progress (27.8 %)
DEBUG: Adding track 3 (fraunhofer) to the queue..
DEBUG: Ripping track 4
DEBUG: Expected filesize for track 4 is 41501084 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/03 - Nocturnes - Nuages  Debussy.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Nocturnes - Nuages / Debussy" --track 3 "/home/shantiq/fraunhofer/temp_sr1/track_3_1.wav"
DEBUG: Free disk space is 152030720 MB
DEBUG: Minutes ripping is 9.106433125699999.
Track  4




DEBUG: cdparanoia [.93235]-[.17644] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_4_1.wav"
Encoding progress (27.8 %)
DEBUG: Removing track 3 (fraunhofer) from the queue..
     Trial 1: 35 seconds (6.67x)
DEBUG: Minutes ripping is 9.694475046233332.
DEBUG: cdparanoia [.93235]-[.17644] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_4_2.wav"
     Trial 2: 52 seconds (4.44x)
DEBUG: Start of hashes algorithm 2014-09-04 11:37:20 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:37:21 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_4_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:37:23 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:37:24 +0100.
     All chunks matched!


     Peak level 91.8 %
     Trial 1 (Copy) CRC 45CB38B3
     Trial 2 (Test) CRC 45CB38B3
     Copy OK


     Copy MD5: afb8dcd28e301aa6d212f843d3e51958


Ripping progress (33 %)
DEBUG: Adding track 4 (fraunhofer) to the queue..
DEBUG: Ripping track 5
DEBUG: Expected filesize for track 5 is 99548444 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/04 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 4 "/home/shantiq/fraunhofer/temp_sr1/track_4_1.wav"
DEBUG: Free disk space is 152052512 MB
DEBUG: Minutes ripping is 10.65233912755.
Track  5




DEBUG: cdparanoia [.110880]-[.42324] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_5_1.wav"
Encoding progress (33 %)
DEBUG: Removing track 4 (fraunhofer) from the queue..
     Trial 1: 113 seconds (4.99x)
DEBUG: Minutes ripping is 12.536769541433333.
DEBUG: cdparanoia [.110880]-[.42324] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_5_2.wav"
     Trial 2: 87 seconds (6.42x)
DEBUG: Start of hashes algorithm 2014-09-04 11:40:46 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:40:50 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_5_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:40:54 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:40:58 +0100.
     All chunks matched!


     Peak level 100.0 %
     Trial 1 (Copy) CRC 9B0253B6
     Trial 2 (Test) CRC 9B0253B6
     Copy OK


     Copy MD5: cdd149144ea166a82e13cc1f1e64b8a4


Ripping progress (45.6 %)
DEBUG: Adding track 5 (fraunhofer) to the queue..
DEBUG: Ripping track 6
DEBUG: Expected filesize for track 6 is 25206428 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/05 - Symphony No 6 - Allegro ma non troppo  Mahler.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Symphony No 6 - Allegro ma non troppo / Mahler" --track 5 "/home/shantiq/fraunhofer/temp_sr1/track_5_1.wav"
DEBUG: Free disk space is 151978568 MB
DEBUG: Minutes ripping is 14.223261888733333.
Track  6




DEBUG: cdparanoia [.153205]-[.10716] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_6_1.wav"
     Trial 1: 34 seconds (4.14x)
DEBUG: Minutes ripping is 14.799139940216666.
DEBUG: cdparanoia [.153205]-[.10716] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_6_2.wav"
Encoding progress (45.6 %)
DEBUG: Removing track 5 (fraunhofer) from the queue..
     Trial 2: 34 seconds (4.11x)
DEBUG: Start of hashes algorithm 2014-09-04 11:42:08 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:42:09 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_6_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:42:10 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:42:11 +0100.
     All chunks matched!


     Peak level 87.6 %
     Trial 1 (Copy) CRC 4D0DD02F
     Trial 2 (Test) CRC 4D0DD02F
     Copy OK


     Copy MD5: db01fc597f7473419a9af1ea43e212aa


Ripping progress (48.8 %)
DEBUG: Adding track 6 (fraunhofer) to the queue..
DEBUG: Ripping track 7
DEBUG: Expected filesize for track 7 is 74617244 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/06 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 6 "/home/shantiq/fraunhofer/temp_sr1/track_6_1.wav"
DEBUG: Free disk space is 152047740 MB
DEBUG: Minutes ripping is 15.4283861246.
Track  7




DEBUG: cdparanoia [.163922]-[.31724] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_7_1.wav"
Encoding progress (48.8 %)
DEBUG: Removing track 6 (fraunhofer) from the queue..
     Trial 1: 53 seconds (7.96x)
DEBUG: Minutes ripping is 16.313992698333333.
DEBUG: cdparanoia [.163922]-[.31724] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_7_2.wav"
     Trial 2: 73 seconds (5.76x)
DEBUG: Start of hashes algorithm 2014-09-04 11:44:18 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:44:20 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_7_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:44:23 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:44:25 +0100.
     All chunks matched!


     Peak level 98.3 %
     Trial 1 (Copy) CRC BE7E5ADB
     Trial 2 (Test) CRC BE7E5ADB
     Copy OK


     Copy MD5: 9e69b4f03b0fac97c528f95f648d75c5


Ripping progress (58.3 %)
DEBUG: Adding track 7 (fraunhofer) to the queue..
DEBUG: Ripping track 8
DEBUG: Expected filesize for track 8 is 26789324 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/07 - Vier Lieder, Op 13  Webern.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Vier Lieder, Op 13 / Webern" --track 7 "/home/shantiq/fraunhofer/temp_sr1/track_7_1.wav"
DEBUG: Free disk space is 152012260 MB
DEBUG: Minutes ripping is 17.6703372429.
Track  8




DEBUG: cdparanoia [.195647]-[.11389] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_8_1.wav"
     Trial 1: 19 seconds (7.86x)
DEBUG: Minutes ripping is 17.992299894533335.
DEBUG: cdparanoia [.195647]-[.11389] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_8_2.wav"
Encoding progress (58.3 %)
DEBUG: Removing track 7 (fraunhofer) from the queue..
     Trial 2: 19 seconds (7.87x)
DEBUG: Start of hashes algorithm 2014-09-04 11:45:04 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:45:05 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_8_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:45:06 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:45:07 +0100.
     All chunks matched!


     Peak level 87.9 %
     Trial 1 (Copy) CRC 9BC6996A
     Trial 2 (Test) CRC 9BC6996A
     Copy OK


     Copy MD5: 63fa42c91600d97dd47d89174b462432


Ripping progress (61.7 %)
DEBUG: Adding track 8 (fraunhofer) to the queue..
DEBUG: Ripping track 9
DEBUG: Expected filesize for track 9 is 65326844 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/08 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 8 "/home/shantiq/fraunhofer/temp_sr1/track_8_1.wav"
DEBUG: Free disk space is 152056292 MB
DEBUG: Minutes ripping is 18.36920439865.
Track  9




DEBUG: cdparanoia [.207037]-[.27774] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_9_1.wav"
Encoding progress (61.7 %)
DEBUG: Removing track 8 (fraunhofer) from the queue..
     Trial 1: 48 seconds (7.66x)
DEBUG: Minutes ripping is 19.17496424606667.
DEBUG: cdparanoia [.207037]-[.27774] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_9_2.wav"
     Trial 2: 58 seconds (6.35x)
DEBUG: Start of hashes algorithm 2014-09-04 11:46:54 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:46:57 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_9_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:47:00 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:47:03 +0100.
     All chunks matched!


     Peak level 100.0 %
     Trial 1 (Copy) CRC 36E9633D
     Trial 2 (Test) CRC 36E9633D
     Copy OK


     Copy MD5: 0803b2ca4588b9e075e58f7c42b24912


Ripping progress (70 %)
DEBUG: Adding track 9 (fraunhofer) to the queue..
DEBUG: Ripping track 10
DEBUG: Expected filesize for track 10 is 19399340 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/09 - Orchestral Pieces, Op 12 - Scherzo  Bartok.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Orchestral Pieces, Op 12 - Scherzo / Bartok" --track 9 "/home/shantiq/fraunhofer/temp_sr1/track_9_1.wav"
DEBUG: Free disk space is 152016392 MB
DEBUG: Minutes ripping is 20.315853562866668.
Track 10




DEBUG: cdparanoia [.234812]-[.8247] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_10_1.wav"
     Trial 1: 23 seconds (4.67x)
DEBUG: Minutes ripping is 20.708051095383333.
DEBUG: cdparanoia [.234812]-[.8247] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_10_2.wav"
Encoding progress (70 %)
DEBUG: Removing track 9 (fraunhofer) from the queue..
     Trial 2: 12 seconds (8.58x)
DEBUG: Start of hashes algorithm 2014-09-04 11:47:41 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:47:41 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_10_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:47:42 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:47:43 +0100.
     All chunks matched!


     Peak level 85.6 %
     Trial 1 (Copy) CRC D9A958E5
     Trial 2 (Test) CRC D9A958E5
     Copy OK


     Copy MD5: 0dfc6d4544a1c2782b6ac9d8591e8a59


Ripping progress (72.4 %)
DEBUG: Adding track 10 (fraunhofer) to the queue..
DEBUG: Ripping track 11
DEBUG: Expected filesize for track 11 is 30352604 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/10 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 10 "/home/shantiq/fraunhofer/temp_sr1/track_10_1.wav"
DEBUG: Free disk space is 152058952 MB
DEBUG: Minutes ripping is 20.960057989150002.
Track 11




DEBUG: cdparanoia [.243060]-[.12904] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_11_1.wav"
Encoding progress (72.4 %)
DEBUG: Removing track 10 (fraunhofer) from the queue..
     Trial 1: 19 seconds (8.77x)
DEBUG: Minutes ripping is 21.287115715716666.
DEBUG: cdparanoia [.243060]-[.12904] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_11_2.wav"
     Trial 2: 33 seconds (5.14x)
DEBUG: Start of hashes algorithm 2014-09-04 11:48:36 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:48:37 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_11_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:48:38 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:48:39 +0100.
     All chunks matched!


     Peak level 96.3 %
     Trial 1 (Copy) CRC 99F11D80
     Trial 2 (Test) CRC 99F11D80
     Copy OK


     Copy MD5: 40391b69eda289ebec0dc4fa909f15cf


Ripping progress (76.3 %)
DEBUG: Adding track 11 (fraunhofer) to the queue..
DEBUG: Ripping track 12
DEBUG: Expected filesize for track 12 is 18333884 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/11 - Chronochromie - Antistrophe I  Messiaen.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Chronochromie - Antistrophe I / Messiaen" --track 11 "/home/shantiq/fraunhofer/temp_sr1/track_11_1.wav"
DEBUG: Free disk space is 152047448 MB
DEBUG: Minutes ripping is 21.903422667133334.
Track 12




DEBUG: cdparanoia [.255965]-[.7794] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_12_1.wav"
Encoding progress (76.3 %)
DEBUG: Removing track 11 (fraunhofer) from the queue..
     Trial 1: 30 seconds (3.37x)
DEBUG: Minutes ripping is 22.41752343035.
DEBUG: cdparanoia [.255965]-[.7794] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_12_2.wav"
     Trial 2: 23 seconds (4.45x)
DEBUG: Start of hashes algorithm 2014-09-04 11:49:34 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:49:34 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_12_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:49:35 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:49:35 +0100.
     All chunks matched!


     Peak level 89.3 %
     Trial 1 (Copy) CRC 0B37BF47
     Trial 2 (Test) CRC 0B37BF47
     Copy OK


     Copy MD5: 1858f7874b6ef6cda20ad68515451729


Ripping progress (78.6 %)
DEBUG: Adding track 12 (fraunhofer) to the queue..
DEBUG: Ripping track 13
DEBUG: Expected filesize for track 13 is 43911884 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/12 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 12 "/home/shantiq/fraunhofer/temp_sr1/track_12_1.wav"
DEBUG: Free disk space is 152057880 MB
DEBUG: Minutes ripping is 22.836292971316666.
Track 13




DEBUG: cdparanoia [.263760]-[.18669] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_13_1.wav"
Encoding progress (78.6 %)
DEBUG: Removing track 12 (fraunhofer) from the queue..
     Trial 1: 27 seconds (8.96x)
DEBUG: Minutes ripping is 23.299518171666666.
DEBUG: cdparanoia [.263760]-[.18669] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_13_2.wav"
     Trial 2: 27 seconds (8.94x)
DEBUG: Start of hashes algorithm 2014-09-04 11:50:31 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:50:32 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_13_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:50:34 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:50:35 +0100.
     All chunks matched!


     Peak level 90.0 %
     Trial 1 (Copy) CRC 5FE198A3
     Trial 2 (Test) CRC 5FE198A3
     Copy OK


     Copy MD5: 7092bbbd45a73f0d41eb98afb39c4113


Ripping progress (84.1 %)
DEBUG: Adding track 13 (fraunhofer) to the queue..
DEBUG: Ripping track 14
DEBUG: Expected filesize for track 14 is 29658764 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/13 - Violin Concerto - Praeludium  Liegeti.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Violin Concerto - Praeludium / Liegeti" --track 13 "/home/shantiq/fraunhofer/temp_sr1/track_13_1.wav"
DEBUG: Free disk space is 152032172 MB
DEBUG: Minutes ripping is 23.839700611.
Track 14




DEBUG: cdparanoia [.282430]-[.12609] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_14_1.wav"
Encoding progress (84.1 %)
DEBUG: Removing track 13 (fraunhofer) from the queue..
     Trial 1: 18 seconds (8.93x)
DEBUG: Minutes ripping is 24.153641796216668.
DEBUG: cdparanoia [.282430]-[.12609] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_14_2.wav"
     Trial 2: 18 seconds (8.92x)
DEBUG: Start of hashes algorithm 2014-09-04 11:51:13 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:51:14 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_14_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:51:15 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:51:16 +0100.
     All chunks matched!


     Peak level 93.2 %
     Trial 1 (Copy) CRC A59214BF
     Trial 2 (Test) CRC A59214BF
     Copy OK


     Copy MD5: 714eaf18d0166998f83ebda19251a931


Ripping progress (87.9 %)
DEBUG: Adding track 14 (fraunhofer) to the queue..
DEBUG: Ripping track 15
DEBUG: Expected filesize for track 15 is 84895484 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/14 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 14 "/home/shantiq/fraunhofer/temp_sr1/track_14_1.wav"
DEBUG: Free disk space is 152044648 MB
DEBUG: Minutes ripping is 24.51546111493333.
Track 15




DEBUG: cdparanoia [.295040]-[.36094] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_15_1.wav"
Encoding progress (87.9 %)
DEBUG: Removing track 14 (fraunhofer) from the queue..
     Trial 1: 62 seconds (7.69x)
DEBUG: Minutes ripping is 25.55792712655.
DEBUG: cdparanoia [.295040]-[.36094] -d /dev/sr1 -O 6 "/home/shantiq/fraunhofer/temp_sr1/track_15_2.wav"
     Trial 2: 92 seconds (5.20x)
DEBUG: Start of hashes algorithm 2014-09-04 11:53:51 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:53:53 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_15_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:53:55 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:53:56 +0100.
     All chunks matched!


     Peak level 99.4 %
     Trial 1 (Copy) CRC A1451300
     Trial 2 (Test) CRC A1451300
     Copy OK


     Copy MD5: fd512a0363a58bf6cbd685ffb1f8c04f


Ripping progress (98.6 %)
DEBUG: Adding track 15 (fraunhofer) to the queue..
DEBUG: Ripping track 16
DEBUG: Expected filesize for track 16 is 10666364 bytes.
DEBUG: LC_ALL=C; df "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70"
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/15 - Une barque sur l'ocean  Ravel.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Une barque sur l'ocean / Ravel" --track 15 "/home/shantiq/fraunhofer/temp_sr1/track_15_1.wav"
DEBUG: Free disk space is 151986804 MB
DEBUG: Minutes ripping is 27.18835997933333.
Track 16




DEBUG: cdparanoia [.331135]-[.4534] -d /dev/sr1 "/home/shantiq/fraunhofer/temp_sr1/track_16_1.wav"
     Trial 1: 16 seconds (3.71x)
DEBUG: Minutes ripping is 27.468561103566667.
DEBUG: cdparanoia [.331135]-[.4534] -d /dev/sr1 "/home/shantiq/fraunhofer/temp_sr1/track_16_2.wav"
Encoding progress (98.6 %)
DEBUG: Removing track 15 (fraunhofer) from the queue..
     Trial 2: 6 seconds (9.14x)
DEBUG: Start of hashes algorithm 2014-09-04 11:54:20 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:54:20 +0100.
DEBUG: LC_ALL=C; sox "/home/shantiq/fraunhofer/temp_sr1/track_16_1.wav" -n stats
DEBUG: Start of hashes algorithm 2014-09-04 11:54:21 +0100.
DEBUG: End of hashes algorithm 2014-09-04 11:54:21 +0100.
     All chunks matched!


     Peak level 84.8 %
     Trial 1 (Copy) CRC 4264A5E6
     Trial 2 (Test) CRC 4264A5E6
     Copy OK


     Copy MD5: 60f3d5cc4597d2d003fed3c1c6938bb8


Ripping progress (100 %)
DEBUG: Adding track 16 (fraunhofer) to the queue..
DEBUG: fdkaac -p 29 -b 38 -o "/home/shantiq/fraunhofer/Boulez (1995) Boulez at 70/16 - Boulez and Plaistow.m4a" --artist "Boulez" --album "Boulez at 70" --genre "Classical" --date "1995" --comment "Rubyripper 0.7.0a1" --title "Boulez and Plaistow" --track 16 "/home/shantiq/fraunhofer/temp_sr1/track_16_1.wav"
Encoding progress (100 %)
DEBUG: Removing track 16 (fraunhofer) from the queue..
No errors occurred
* RUBYRIPPER MAIN MENU *


 1) Change preferences
 2) Scan drive for audio disc
 3) Change metadata
 4) Select the tracks to rip (default = all)
 5) Rip the disc!
99) Exit rubyripper...


Please type the number of your choice [99] : DEBUG: eject /dev/sr1


Thanks for using rubyripper.
Have a nice day!

```


> GeneralComplete name                            : 01 - No Room For Doubt (feat. Willy Mason).m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 1.12 MiB
Duration                                 : 4mn 2s
Overall bit rate mode                    : Variable
Overall bit rate                         : 38.8 Kbps
Album                                    : Lost & Found EP
Track name                               : No Room For Doubt (feat. Willy Mason)
Track name/Position                      : 1
Performer                                : Lianne La Havas
Genre                                    : Rock
Recorded date                            : 2011
Encoded date                             : UTC 2013-08-15 08:01:35
Tagged date                              : UTC 2013-08-15 08:01:35
Writing application                      : fdkaac 0.2.0, libfdk-aac 3.3.3, CBR 38kbps
Comment                                  : Rubyripper 0.7.0a1


Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AACv2 / HE-AAC / LC
Codec ID                                 : 40
Duration                                 : 4mn 2s
Bit rate mode                            : Variable
Bit rate                                 : 38.0 Kbps
Maximum bit rate                         : 41.1 Kbps
Channel(s)                               : 2 channels / 1 channel / 1 channel
Channel positions                        : Front: L R / Front: C / Front: C
Sampling rate                            : 44.1 KHz / 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 1.10 MiB (98%)
Encoded date                             : UTC 2013-08-15 08:01:35
Tagged date                              : UTC 2013-08-15 08:01:35




---

### Post by shantiq on 2013-11-24
on 13.10


use 7.0 from post [52]("http://ubuntuforums.org/showthread.php?t=1533534&p=12757438#post12757438")  or try 0.6.2.1 need a couple of dependencies

```
sudo apt-get install cd-discid ruby-gtk2  ruby-gettext
```

```
[noparse] wget http://launchpadlibrarian.net/121572808/libgettext-ruby1.8_2.2.1-3_all.deb ; sudo dpkg -i libgettext-ruby1.8_2.2.1-3_all.deb[/noparse]
```

```
 [noparse]wget http://launchpadlibrarian.net/57809893/libgettext-ruby-util_2.1.0-2.1ubuntu1_all.deb ; sudo dpkg -i libgettext-ruby-util_2.1.0-2.1ubuntu1_all.deb[/noparse]
```

```
[noparse] wget http://archive.getdeb.net/getdeb/ubuntu/pool/apps/r/rubyripper/rubyripper_0.6.2-1~getdeb1_all.deb ; sudo dpkg -i rubyripper_0.6.2-1~getdeb1_all.deb[/noparse]
```



**ps** : Other line[ encoders]("http://ubuntuforums.org/showthread.php?t=1533534&p=9630448#post9630448") updated

change easily  ```
gedit .config/rubyripper/settings
```

---

### Post by burke3gd on 2013-12-15
> **shantiq said:**
> and yes mc4man you are right again works with alac beautifully:KS:KS


```
ffmpeg  -i %i -acodec alac  "%o".m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track="%n" -meta:title="%t
```


This was of great help to me, but I've since simplified it a bit. Also, the metadata tag for the year should actually be "DATE".

Here's my recipe for encoding with ALAC, it requires only **avconv** (ffmpeg's replacement in Ubuntu):

```
avconv  -i %i -codec alac -metadata ARTIST=%a -metadata ALBUM=%b -metadata GENRE=%g -metadata DATE=%y -metadata TRACK=%n -metadata TITLE=%t %o.m4a
```

---

### Post by shantiq on 2013-12-16
excellent burke i have added to [summary]("http://ubuntuforums.org/showthread.php?t=1533534&p=9630448#post9630448")
well spotted on date versus year too; never understood the difference :)


added comment option too [ffmpeg or avconv]

> ffmpeg  -i %i -codec alac -metadata ARTIST=%a -metadata ALBUM=%b -metadata GENRE=%g -metadata DATE=%y -metadata TRACK=%n -metadata TITLE=%t -metadata COMMENT="Ripped.Rubyripper.By.Yourname" %o.m4a

---

### Post by andr12 on 2014-11-20
Is it possible to use the "other codec" option to encode to mp3 in another bitrate than what I have in the standard mp3 line? 

What should I put in that line?

Edit:
Nevermind, I figured it out: 

> lame -b<bitrate> "%i" "%o".mp3 --ta "%a" --tt "%t" --tg "%g" --tl "%b" --ty "%y" --tn "%n" --id3v2-only

---

### Post by andrew.46 on 2014-12-18
Shan: Is it a better option to encode with alac under Linux to use qaac with the --alac option rather than FFmpeg's encoder? My old ears can hear a certain richness of the audio with qaac / CoreAudioToolbox output...

---

### Post by shantiq on 2014-12-19
wow Andrew must confess i av not tested both ...    chance of a blind test of say one minute of the same unmarked uploaded here ?     see   if a sample of testers can tell the difference AND agree    it will be cool   fancy a try?

---

### Post by andrew.46 on 2014-12-19
Sounds good :)

---

### Post by shantiq on 2014-12-19
i mean Andrew : **you** got some ready samples please?   ::]]

---

### Post by andrew.46 on 2014-12-19
I have created 2 samples, one using qaac and one using FFmpeg, it will be pretty obvious which is which from the metatags (which I have not tried to mask). Having listened carefully to each I have to say that it is very close but my money is still on the qaac file :).

```

wget http://www.andrews-corner.org/samples/luckynight_1.m4a
wget http://www.andrews-corner.org/samples/luckynight_2.m4a

```

It would be interesting to hear from someone with decent sound equipment and young, discerning ears. I have neither!

---

### Post by shantiq on 2014-12-20
Thanx Andrew   number 2 is way clearer feels closer    number one feels thinner

running it with cvlc shows no tags whatsoever so totally blind

see

```
shantiq@shantiq-00000000000000000000000:~$ wget http://www.andrews-corner.org/samples/luckynight_1.m4a--2014-12-20 06:57:11--  http://www.andrews-corner.org/samples/luckynight_1.m4a
Resolving www.andrews-corner.org (www.andrews-corner.org)... 173.236.188.207
Connecting to www.andrews-corner.org (www.andrews-corner.org)|173.236.188.207|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6693447 (6.4M) [text/plain]
Saving to: ‘luckynight_1.m4a’


100%[======================================>] 6,693,447   1.07MB/s   in 6.7s   


2014-12-20 06:57:18 (983 KB/s) - ‘luckynight_1.m4a’ saved [6693447/6693447]


shantiq@shantiq-00000000000000000000000:~$ wget http://www.andrews-corner.org/samples/luckynight_2.m4a
--2014-12-20 06:57:21--  http://www.andrews-corner.org/samples/luckynight_2.m4a
Resolving www.andrews-corner.org (www.andrews-corner.org)... 173.236.188.207
Connecting to www.andrews-corner.org (www.andrews-corner.org)|173.236.188.207|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6714666 (6.4M) [text/plain]
Saving to: ‘luckynight_2.m4a’


100%[======================================>] 6,714,666   1003KB/s   in 10s    


2014-12-20 06:57:31 (659 KB/s) - ‘luckynight_2.m4a’ saved [6714666/6714666]


shantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_1.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x1e44d28] dummy interface: using the dummy interface module...


(process:3244): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3244): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed


(process:3244): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3244): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^Z
[1]+  Stopped                 cvlc luckynight_1.m4a
shantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_2.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xa56cc8] dummy interface: using the dummy interface module...


(process:3298): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3298): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^Z[1]   Killed                  cvlc luckynight_1.m4a


[2]+  Stopped                 cvlc luckynight_2.m4a
shantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_2.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x1041d48] dummy interface: using the dummy interface module...


(process:3315): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3315): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^C[2]+  Killed                  cvlc luckynight_2.m4a
shantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_1.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x18b3d08] dummy interface: using the dummy interface module...


(process:3330): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3330): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^Cshantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_2.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x1798cc8] dummy interface: using the dummy interface module...


(process:3341): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3341): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^Cshantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_1.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0xe30d28] dummy interface: using the dummy interface module...


(process:3353): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(process:3353): Gtk-CRITICAL **: IA__gtk_icon_theme_load_icon: assertion 'GTK_IS_ICON_THEME (icon_theme)' failed
^Cshantiq@shantiq-00000000000000000000000:~$ cvlc luckynight_2.m4a
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)





```

---

### Post by mc4man on 2014-12-20
In a completely blind but likely not best equipment wise test I'd lean towards #2 though both quite similar
(- was on the road so played the url's directly with vlc in a nexus 7 piped to car's audio system.
Now that I'm home will have to try them thru stereo system in a little while & also see which was what.

---

### Post by andrew.46 on 2015-06-19
Speaking of qaac I have started working on incorporating qaac into abcde and in preparation for the many who will not know how to install qaac correctly I have created a more 'Linux' way of accomplishing it (borrowing from makeportable.bat):

Using qaac under Linux...
[http://www.andrews-corner.org/qaac.html](http://www.andrews-corner.org/qaac.html)

Still a lot of work to do there but I quite like the installation method! I will hunt around for an easy method of installing libFLAC.dll, wavpackdll.dll, tak_deco_lib.dll, and libsndfile-1.dll to complete the picture. And of course wrestle with abcde itself...

---

### Post by shantiq on 2015-06-19
ace Andrew means we will have another access to alac that way!    best of luck
I use qaac.exe in EAC under wine for that purpose
will be nice to go Linux on that too

---

