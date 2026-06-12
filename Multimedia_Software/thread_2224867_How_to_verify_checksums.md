---
title: "How to verify checksums"
date: 2014-05-18
forum: Multimedia Software
---

### Post by cicada2 on 2014-05-18
I am new to Lubuntu and love it so far. One task that i have not figured out - how to verify checksums for all my audio files (mostly flac and shn)? When I get these files they come with ffp's, md5's and st5's.

I have tried md5sum to check the md5 files but I get this error:
:FAILED open or read
:No such file or directory

I have removed all spaces from the folders and tweaked the title of the md5 file so I can navigate in the terminal window. All the ones I have tried have simple track names (with no spaces)... I did not change tracknames and they seem to match the labels in the md5 file.

Any help is greatly appreciated!

---

### Post by sudodus on 2014-05-18
The simple command is

```

[COLOR=#0000ff]md5sum Pott-Konzert.wmv [/COLOR]
18b9b204dd0cef5c47c2a0db4b493e4c  Pott-Konzert.wmv

```

for visual inspection.

That output can be put into a file, and you can put the md5sums of all files in a directory into the same file.

```

[COLOR=#0000ff]md5sum Pott-Konzert.wmv > md5sum.txt[/COLOR]
[COLOR=#0000ff]
cat md5sum.txt[/COLOR]
18b9b204dd0cef5c47c2a0db4b493e4c  Pott-Konzert.wmv

```
and```

[COLOR=#0000ff]md5sum * > md5sum.txt[/COLOR]
[COLOR=#0000ff]
cat md5sum.txt[/COLOR]
18b9b204dd0cef5c47c2a0db4b493e4c  Pott-Konzert.wmv
...
...

```

and you can check automatically with this command

```
[COLOR=#0000ff]
md5sum -c md5sum.txt[/COLOR]
Pott-Konzert.wmv: OK
...
...

```

See this description of the method[URL="https://help.ubuntu.com/community/UbuntuHashes"]

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[/URL]

---

### Post by cicada2 on 2014-05-18
Thanks sudodus! Any suggestions for ffp or st5 checksums? 

The instructions above work fine. I compared my new results with those md5 cheksums that came with the original filesets & they were the same... except the 2 were formatted a little differently. 
_my md5_
ff6b17754d5fa122784f55a72bfe2c53  Track0101.flac
_orig md5_
ff6b17754d5fa122784f55a72bfe2c53 *Track0101.flac
...
...
...

So I get errors when I try to check the ***original checksums***. No big deal. I can see that they match. I tried removing the asterisk and adding 1 space to manually correct the original format and i cannot get the original checksums to check without an error. I guess this is a formatting error of some kind? Would be nice to use the original checksums to verify the filesets without having to generate my own and then manually comparing them to see that they match. Any suggestions?

---

### Post by sudodus on 2014-05-19
If you make your own checksum files, use a method, so that there are ***two spaces or a space and a star*** between the sum and the name. If there is only one space, it will not work with

```
md5sum -c md5sums.txt
```

I think that all checksums are good enough for checking that the copying or downloading was successful. For security reasons, you should have a longer checksum (so sha256sum is better than md5sum).

[http://askubuntu.com/questions/172947/what-are-the-differences-between-md5sum-and-sha256sum](http://askubuntu.com/questions/172947/what-are-the-differences-between-md5sum-and-sha256sum)

---

### Post by cicada2 on 2014-05-19
Can you think of any reason why I got a failure for the checksums with the asterisk (see above)?
 
It would be preferable to simply run the md5 check since I already have md5 files. I mean, why create new files if all that is needed is to check existing? My problem is the failure (even though they are a match). I tried removing the asterisk (inserting exactly 2 spaces)... but that doesn't work either. What am I missing?

Thank you!

---

### Post by sudodus on 2014-05-19
Please show exactly what command you used when the md5sum check failed!

And what does the file with checksums look like?

---

### Post by cicada2 on 2014-05-19
I used this command:
[COLOR=#0000ff]md5sum -c my.txt[/COLOR]
Here are the checksums I was testing

58b83c0c14c49efbf197bd3badb50ab2 *Nils Lofgren Bottom Line NY 10-28-77.txt
ff6b17754d5fa122784f55a72bfe2c53 *Track0101.flac
8c3e1aba7602bdc89165a62a822c2bb4 *Track0102.flac
0bc926e1b33bfb0bcec792b5c5ab5374 *Track0103.flac
8d60e23b30f65bb868c95f1c16b18cdb *Track0104.flac
9147ada3bde1430c648fa1643fe9943d *Track0105.flac
ace208eb6184459f83c7f0276dbf46e8 *Track0106.flac
e5a6283b50ff52c759eb2333e4b05e94 *Track0107.flac
b55276800b5294543d26219d513330e7 *Track0108.flac
81561a7dc30d120b01e0be6f6a5c7a0b *Track0109.flac
f2bff0110536642b8f7420229ebf3c12 *Track0110.flac
4489b69a1cc07dbc208284d96fe8f33b *Track0111.flac
5bd00979db749423c1192753281eb987 *Track0112.flac
264a32d1eee9004a32a3eb6aefe7226c *Track0113.flac
d2b6e5bd5e2c5175c82022318dd25bdc *Track0114.flac
be6ff2fd6e21c6deb4f0a001b5cae1b7 *Track0115.flac

---

### Post by sudodus on 2014-05-20
I made md5star.txt to be like this

```
cat md5star.txt
18b9b204dd0cef5c47c2a0db4b493e4c *Pott-Konzert.wmv

```
and it works too (for me)

```
md5sum -c md5star.txt
Pott-Konzert.wmv: OK
```

- What is your output (instead of filename: OK)?
- Are the files in the current directory?
- Is there a problem with the file name that contains spaces?

---

### Post by cicada2 on 2014-05-20
I am not sure how to answer, "what is your output (instead of filename). Sorry I am just learning here. 

The files are in this directory (not is subfolders or anything). There are no spaces. Since the first md5 contained a filename with spaces, I removed it and then renamed the file md5star.txt. Here is what appears in the terminal window.
[email]cicada@cicada-Presario-R3000-DS514U-ABL:/media/extJ/temp/aarock1/lofgren77-10-28.fm.flac[/email]16_Bottom_Line,NYC_hc$ md5sum -c md5star.txt
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
md5sum: WARNING: 15 listed files could not be read

---

### Post by sudodus on 2014-05-20
It seems that the file names are wrong in the file **md5star.txt** or that you are running it in the wrong directory.

Use ```
cd directory-name
``` (with the correct directory name) to change directory to where you store the flac files.

---

### Post by cicada2 on 2014-05-20
I sure do appreciate all your patience. Please tell me if you think I am missing something. Here is a list of everything in this directory (Md5star is bold).

[email]cicada@cicada-Presario-R3000-DS514U-ABL:/media/extJ/temp/aarock1/lofgren77-10-28.fm.flac[/email]16_Bottom_Line,NYC_hc$ ls
**md5star.txt  **                               Track0104.flac  Track0111.flac
md5sum.txt                                  Track0105.flac  Track0112.flac
Nils Lofgren Bottom Line NY 10-28-77.txt    Track0106.flac  Track0113.flac
Nils Lofgren Bottom Line WBCN 10-28-77.md5  Track0107.flac  Track0114.flac
Track0101.flac                              Track0108.flac  Track0115.flac
Track0102.flac                              Track0109.flac
Track0103.flac                              Track0110.flac

---

### Post by sudodus on 2014-05-20
Let us say that your files are in the directory Music (in the home directory)

Try according to these commands (change it to find ***your*** txt and flac files)

```
cd $HOME/Music
ls -l
```
Do you see your txt files and flac files?

If yes, continue, otherwise change directory until you are in the correct directory.

```
cat md5star.txt
cat md5sum.txt

```
Post the lists from these commands. Please put them within code tags: Go Advanced (red button below the editing window). Mark the text. Click on the **#** icon above the editing window.

Run this command

```
md5sum *

```Post the lists from this command. Please put it within code tags.

Run these commands

```
md5sum -c md5sum.txt
md5sum -c md5star.txt

```
Post the lists from these commands. Please put them within code tags.

---

### Post by cicada2 on 2014-05-20
> **sudodus said:**
> 
```
cd $HOME/Music
ls -l
```
Do you see your txt files and flac files?

Yes. All good.

> **sudodus said:**
> [COLOR=#000000]
[/COLOR]```
[COLOR=#000000]
cat md5star.txt
cat md5sum.txt[/COLOR]
```
[COLOR=#000000]Post the lists from these commands. Please put them within code tags:[/COLOR]


Works like a charm.
```
cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ cat md5star.txtff6b17754d5fa122784f55a72bfe2c53 *Track0101.flac
8c3e1aba7602bdc89165a62a822c2bb4 *Track0102.flac
0bc926e1b33bfb0bcec792b5c5ab5374 *Track0103.flac
8d60e23b30f65bb868c95f1c16b18cdb *Track0104.flac
9147ada3bde1430c648fa1643fe9943d *Track0105.flac
ace208eb6184459f83c7f0276dbf46e8 *Track0106.flac
e5a6283b50ff52c759eb2333e4b05e94 *Track0107.flac
b55276800b5294543d26219d513330e7 *Track0108.flac
81561a7dc30d120b01e0be6f6a5c7a0b *Track0109.flac
f2bff0110536642b8f7420229ebf3c12 *Track0110.flac
4489b69a1cc07dbc208284d96fe8f33b *Track0111.flac
5bd00979db749423c1192753281eb987 *Track0112.flac
264a32d1eee9004a32a3eb6aefe7226c *Track0113.flac
d2b6e5bd5e2c5175c82022318dd25bdc *Track0114.flac
be6ff2fd6e21c6deb4f0a001b5cae1b7 *Track0115.flac
cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ cat md5sum.txt
ee1b3241befaaab4e3e0bd917e7dd73f  my.txt
58b83c0c14c49efbf197bd3badb50ab2  Nils Lofgren Bottom Line NY 10-28-77.txt
ee1b3241befaaab4e3e0bd917e7dd73f  Nils Lofgren Bottom Line WBCN 10-28-77.md5
ff6b17754d5fa122784f55a72bfe2c53  Track0101.flac
8c3e1aba7602bdc89165a62a822c2bb4  Track0102.flac
0bc926e1b33bfb0bcec792b5c5ab5374  Track0103.flac
8d60e23b30f65bb868c95f1c16b18cdb  Track0104.flac
9147ada3bde1430c648fa1643fe9943d  Track0105.flac
ace208eb6184459f83c7f0276dbf46e8  Track0106.flac
e5a6283b50ff52c759eb2333e4b05e94  Track0107.flac
b55276800b5294543d26219d513330e7  Track0108.flac
81561a7dc30d120b01e0be6f6a5c7a0b  Track0109.flac
f2bff0110536642b8f7420229ebf3c12  Track0110.flac
4489b69a1cc07dbc208284d96fe8f33b  Track0111.flac
5bd00979db749423c1192753281eb987  Track0112.flac
264a32d1eee9004a32a3eb6aefe7226c  Track0113.flac
d2b6e5bd5e2c5175c82022318dd25bdc  Track0114.flac
be6ff2fd6e21c6deb4f0a001b5cae1b7  Track0115.flac

```

> **sudodus said:**
> 
[COLOR=#000000]Run this command[/COLOR]

```
[COLOR=#000000]
md5sum *[/COLOR]
```[COLOR=#000000]
[/COLOR]
Here is the info posted below.
```
cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ md5sum *31df9cc1f07edb72f742427679a54db1  140512_CICADALIST.xls
4912ae012e03e7e5e83c1fcf7bf88c07  md5star.txt
08ae870526922378d0c8a65cb5319397  md5sum.txt
58b83c0c14c49efbf197bd3badb50ab2  Nils Lofgren Bottom Line NY 10-28-77.txt
ee1b3241befaaab4e3e0bd917e7dd73f  Nils Lofgren Bottom Line WBCN 10-28-77.md5
ff6b17754d5fa122784f55a72bfe2c53  Track0101.flac
8c3e1aba7602bdc89165a62a822c2bb4  Track0102.flac
0bc926e1b33bfb0bcec792b5c5ab5374  Track0103.flac
8d60e23b30f65bb868c95f1c16b18cdb  Track0104.flac
9147ada3bde1430c648fa1643fe9943d  Track0105.flac
ace208eb6184459f83c7f0276dbf46e8  Track0106.flac
e5a6283b50ff52c759eb2333e4b05e94  Track0107.flac
b55276800b5294543d26219d513330e7  Track0108.flac
81561a7dc30d120b01e0be6f6a5c7a0b  Track0109.flac
f2bff0110536642b8f7420229ebf3c12  Track0110.flac
4489b69a1cc07dbc208284d96fe8f33b  Track0111.flac
5bd00979db749423c1192753281eb987  Track0112.flac
264a32d1eee9004a32a3eb6aefe7226c  Track0113.flac
d2b6e5bd5e2c5175c82022318dd25bdc  Track0114.flac
be6ff2fd6e21c6deb4f0a001b5cae1b7  Track0115.flac

```

> **sudodus said:**
> 
[COLOR=#000000]Run these commands[/COLOR]

[COLOR=#000000]```

md5sum -c md5sum.txt
md5sum -c md5star.txt[/COLOR][COLOR=#000000]
[/COLOR]
The final check...
[CODE]cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ md5sum -c md5sum.txtmd5sum: my.txt: No such file or directory
my.txt: FAILED open or read
Nils Lofgren Bottom Line NY 10-28-77.txt: OK
Nils Lofgren Bottom Line WBCN 10-28-77.md5: OK
Track0101.flac: OK
Track0102.flac: OK
Track0103.flac: OK
Track0104.flac: OK
Track0105.flac: OK
Track0106.flac: OK
Track0107.flac: OK
Track0108.flac: OK
Track0109.flac: OK
Track0110.flac: OK
Track0111.flac: OK
Track0112.flac: OK
Track0113.flac: OK
Track0114.flac: OK
Track0115.flac: OK
md5sum: WARNING: 1 listed file could not be read
cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ md5sum -c md5star.txt
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
md5sum: WARNING: 15 listed files could not be read

```

md5sum.txt are the checksums I generated per your instructions. 
md5star.txt are the checksums that came with the fileset originally

---

### Post by sudodus on 2014-05-21
From the manual ```
man md5sum
``` we can read

       ```

The  sums  are  computed as described in RFC 1321.  When checking, the input should be a former
       output of this program.  The default mode is to print a line with checksum, a  character  indi&#8208;
       cating type (`*' for binary, ` ' for text), and name for each FILE.

```

It works for me with two spaces and with one space and one star. I run Ubuntu 12.04 LTS with md5sum version 8.13

```

[COLOR=#0000ff]md5sum --version[/COLOR]
md5sum (GNU coreutils) 8.13

```

I think the star is probably confusing your version of md5sum. What version of Ubuntu are you running, and what version of md5sum?

What you can do is replacing the star with a space. You can do that for all the lines with the stream editor sed

```
sed 's/*/ /' md5star.txt > md5clean.txt
```

and try

```

md5sum -c md5clean.txt

```

or pipe '|' the sed result into md5sum directly

```

[COLOR=#0000ff]sed 's/*/ /' md5star.txt | md5sum -c[/COLOR]
Pott-Konzert.wmv: OK

```

I tested it with the same example as in post #2, and as you can see from the result. I think it will work for you too.

---

### Post by cicada2 on 2014-05-21
All new installs...
md5sum (GNU coreutils) 8.13
Ubuntu 12.04.4 LTS

Previously, I tried using 2 spaces (after removing the asterisk), but it didn't work for me. I just executed the change to md5clean... and I still got a failure. It's got me baffled.
```
cicada@cicada-Presario-R3000-DS514U-ABL:~/Music$ md5sum -c md5clean.txt
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
: No such file or directory
: FAILED open or read
md5sum: WARNING: 15 listed files could not be read

```

---

### Post by sudodus on 2014-05-21
Could it be that the original md5sum file, md5star.txt, was created in another operating system, Windows or MacOS? In that case there might be a trailing character belonging to the change to a new line.

- Linux has only one character, line-feed, ascii 10 (decimal), 0A (hexadecimal), '0A'
- Windows has two characters, carriage return, ascii 13 (decimal), 0D (hexadecimal) and line-feed, ascii 10 (decimal), '0D 0A'
- MacOS has something else that I don't remember now

You can check in a binary editor (hex editor), for example you can install Midnight Commander ***mc***, high-light the file and view it with the F3 key and toggle between hex and ascii with the F4 key.

```
sudo apt-get install mc
```

If this is the case you can convert the file to unix with dos2unix

```
sudo apt-get install dos2unix 
```

See this link where the options are explained, and it seems possible to also convert from Mac

[http://linux.about.com/od/commands/l/blcmdl1_dos2uni.htm](http://linux.about.com/od/commands/l/blcmdl1_dos2uni.htm)

```
**-c --convmode convmode**  
 Sets conversion mode. Simulates dos2unix under SunOS. 
  Convert and replace a.txt in ASCII conversion mode.  Convert and replace b.txt in ISO conversion mode. Convert c.txt from Mac to Unix ascii format. 

 **dos2unix a.txt -c iso b.txt**  
 **dos2unix -c ascii a.txt -c iso b.txt**  
 **dos2unix -c mac a.txt  b.txt**

```

---

### Post by cicada2 on 2014-05-21
I am almost positive the original file was created by windoze (or mac). This will be the norm for files I intend to work with in the future.  

I am happy to report a solution that works for all my checksums (ffp, md5 & st5)... even when they were generated by my friends' with windoze and mac. There is** etree-scripts**. Details about this - along with some other music sharing software for Linux are found here... [http://etree.org/linux.html](http://etree.org/linux.html). The deb file can be found at sourceforge... [http://etree-scripts.sourceforge.net](http://etree-scripts.sourceforge.net).  I didn't have to do anything special to verify these and other checksums. For some reason this works for me, so that will be my solution. 

Thanks to sudodus for working with me to resolve this. Your patience and knowledge are greatly appreciated!

---

### Post by sudodus on 2014-05-21
Congratulations :KS

I'm glad you found a convenient tool-box, **etree-scripts**. I looked at it and I guess that [FONT=Arial][SIZE=2][FONT=Verdana,Arial,Helvetica][SIZE=1][FONT=Verdana,Arial,Helvetica][SIZE=1][FONT=Arial][SIZE=2]**md5check **is what you use, and that it can manage different ways to represent the transfer from one line to the next one.[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

