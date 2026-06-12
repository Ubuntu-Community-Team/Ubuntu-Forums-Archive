---
title: "IDX/SUB to SRT"
date: 2022-07-30
forum: Multimedia Software
---

### Post by John Jason Jordan on 2022-07-30
Xubuntu 20.04, up to date, but waiting for the dist-upgrade to 22.04.

I need to do this now and then, but could never find a way to do it with Linux. However, for a long time I have occasionally used 

[https://subconverter.com/convert-sub-idx-to-srt-online]("https://subconverter.com/convert-sub-idx-to-srt-online")

Which has worked very well. But while I appreciate their efforts, they now demand a subscription with an automatic monthly payment from Paypal. I've been down that road. No thanks. 

So now I'm back trying to find a way to do it with Ubuntu. The only thing I have found is vobsub2srt, but it doesn't work. For example, my current sub/idx files are x.sub and x.idx, and it's supposed to work with the command 'vobsub2srt x.' All I can get is an error message:

```
vobsub2srt: error while loading shared libraries: libtesseract.so.3: cannot open shared object file: No such file or directory
```

I tried putting being sure I'm in the folder where the files are located, and even adding the full path to the command, but no luck. I also reinstalled tesseract, but still get the same error message.

I hate these stinky fuzzy sub images. I hope I can come up with a solution. :)

---

### Post by John Jason Jordan on 2022-07-30
No solution yet, but I think I understand the error message a bit better. From the message I couldn't understand if it couldn't find the sub/idx files, or if it couldn't find libtesseract.so.3. Now I think it's libtesseract.so.3 that is missing, but I don't know what to do about it. I can't figure out where libtesseract.so.3 is supposed to come from - it's not a separate package listed in Synaptic.

Code:
sudo apt install tesseract-ocr
tesseract-ocr is already the newest version (4.1.1-2build2).
sudo apt install libtesseract.so.3
E: Unable to locate package libtesseract.so.3

It looks like it might be a mismatch between the installed version of vobsub2srt and the installed version of tesseract-ocr. I could use some suggestions.

---

### Post by TheFu on 2022-07-31
It has been a few years, but avidemux will convert the image-subs from glyphs into text.  Some training is required, but it gets better and better since the glyph -to- character mapping can be retained between runs.

[https://archive.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles.html](https://archive.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles.html) shows the steps.

Beware that it seems every DVD author like to use their own fonts for subtitle images, so it is likely that you'll need to keep training for some time so there aren't **any** stops for human input during the OCR step.

---

### Post by #&amp;thj^% on 2022-07-31
Just to add to TheFu's suggestion, There is an app called SubtitleEdit. It uses tesseract as backend for OCR stuff. [https://www.nikse.dk/subtitleedit](https://www.nikse.dk/subtitleedit)
also vobsub2srt. It is command line only tool which also uses tesseract. [https://github.com/ruediger/VobSub2SRT](https://github.com/ruediger/VobSub2SRT)
however I don't feel it's maintained very well, >> last change was 5-7 years ago. **As the OP has found.**

---

### Post by John Jason Jordan on 2022-07-31
> **TheFu said:**
> It has been a few years, but avidemux will convert the image-subs from glyphs into text.  Some training is required, but it gets better and better since the glyph -to- character mapping can be retained between runs.

[https://archive.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles.html](https://archive.flossmanuals.net/avidemux/ch019_extract-dvd-subtitles.html) shows the steps.

Beware that it seems every DVD author like to use their own fonts for subtitle images, so it is likely that you'll need to keep training for some time so there aren't **any** stops for human input during the OCR step.

I had already tried Avidemux and given up on it. When I saw your link to flossmanuals I hoped that I might finally have something that would help, but the instructions there are apparently for an unknown version that is not the same as mine. First, the instructions start with pages of information for extracting sub/idx from a DVD, but I skipped past that, as I already have sub/idx files. Then I got to 'Making the srt file' and immediately ran into an impasse. It says to go to Tools' and then 'OCR (VobSub -> Srt), which is supposed to pop up  window labeled MiniOCR, but what I get is a window labeled 'Select input and output files.' Unfortunately, it only allows selecting the .idx file, although when I did it popped up a window showing what was apparently the first line of the sub/idx files, so somehow it must have gotten the .sub file as well. But the window did not display timing information, and if you want to select the line you can only do it one letter at a time. Most movie subtitle files are at least a thousand lines of 20-40 characters each, so this might take a year of my life. If I could have just typed the line somewhere it might be usable, but there is no way to do that. Avidemux probably has many cool features, but the user interface is hopeless, there are no detailed instructions, and the interface is completely different for every version. 

I have subtitle editors: BDSup2Sub, Gaupol, Gnome Subtitles, Jubler, and 'Subtitle Editor,' which is what I usually use. A couple of them are unusable because my screen is 2160p (4K), and the programmer hard coded the size of all text to a size that is readable only with a magnifying glass. The Settings and Preferences offer no way to adjust font size. I'm serious - the font is about 1mm high on screen. It would be uncomfortably small even on an FHD 1080p screen.

Sorry for being so negative. I'm just frustrated.

---

### Post by John Jason Jordan on 2022-07-31
> **1fallen said:**
> Just to add to TheFu's suggestion, There is an app called SubtitleEdit. It uses tesseract as backend for OCR stuff. [https://www.nikse.dk/subtitleedit](https://www.nikse.dk/subtitleedit)
also vobsub2srt. It is command line only tool which also uses tesseract. [https://github.com/ruediger/VobSub2SRT](https://github.com/ruediger/VobSub2SRT)
however I don't feel it's maintained very well, >> last change was 5-7 years ago. **As the OP has found.**

Thanks for the suggestion, but no way am I going to install Mono or Wine. :(

---

### Post by #&amp;thj^% on 2022-07-31
> **John Jason Jordan said:**
> Thanks for the suggestion, but no way am I going to install Mono or Wine. :(
I guess that wasn't the best link to show you but it is available on linux via: Snap : [https://snapcraft.io/install/subtitle-edit/ubuntu](https://snapcraft.io/install/subtitle-edit/ubuntu)
[S]Or a better Link: [https://www.nikse.dk/subtitleedit/help#linux](https://www.nikse.dk/subtitleedit/help#linux)[/S]
Ok No mono then ;)  [https://www.ubuntupit.com/best-subtitle-editor-for-linux/](https://www.ubuntupit.com/best-subtitle-editor-for-linux/)

---

### Post by TheFu on 2022-07-31
I understand the frustration.  Trust me, avidemux when it asks for 1 character at a time, it is because you don't already have a glyph file with the prior characters.  But it gets better.  You'll have to train 96 characters on the first file, then more like 10 characters each on the next 5 files, as the different fonts are seen and OCR can't figure out if it is an i or an l or 1.

It gets better and smarter and faster.  Pretty soon, within the first 1 files, if the language and sub fonts are the same, you'll barely have to add any glyph -to- character training at all.

---

### Post by John Jason Jordan on 2022-07-31
> **TheFu said:**
> I understand the frustration.  Trust me, avidemux when it asks for 1 character at a time, it is because you don't already have a glyph file with the prior characters.  But it gets better.  You'll have to train 96 characters on the first file, then more like 10 characters each on the next 5 files, as the different fonts are seen and OCR can't figure out if it is an i or an l or 1.
It gets better and smarter and faster.  Pretty soon, within the first 1 files, if the language and sub fonts are the same, you'll barely have to add any glyph -to- character training at all.

With Avidemux it's the user interface that is just about impossible for me. But I finally found something that does the job: Subtitle Composer, in the repos. It will open an idx/sub file and display the text. It's sort of like the little window that pops up in Avidemux, and it's slow at first, one character at a time, but it got lots better really fast. Unlike Avidemux it is a real subtitle editor, even with spell checking and everything was right in the normal places, like to save the file you go to File > Save, or File > Save As. And text was normal size. The idx/sub files that I was working on had just under a thousand lines and the OCR part took about 15 minutes to get to line 100, by which time it was stopping for input on only two or three letters per line. Eventually it started skipping over 10-15 lines at a time, and finally it zoomed all the way to the end. Lots of errors, but the timings were all there and I was looking at an ordinary .srt file.. The spell checker took a couple hours, because I had to fix three or four words per line, but it always had a list of suggestions, and three out of four were correct, so mostly all I had to do was click on Replace.

Subtitle Composer must be using tesseract-ocr, because how else could it be doing the OCR? But the process was 100% transparent, nothing to add or configure; it *just works*. I don't know how/where it is saving the glyphs, but I hope it is doing so. When I finished I just closed it down, and there was no prompt to save a glyph file. We'll see what happens next time.

At least now I have a way to create a .srt from idx/sub. Not as easy or as accurate as that web based place, but their pay subscription scheme lost me. And maybe Subtitle Composer will eventually equal it in accuracy.

---

### Post by TheFu on 2022-08-01
Thanks for sharing the better solution!  I'll need to try that out and hope it works better. I haven't used a disc in years now. Ripped all our DVDs long ago so we watch those and stream other content.  Some streaming provides captions and others provide 'burned in' subtitles.  The captions (SRT/ASS) can be requested separately using tools we cannot discuss in these forums.

---

### Post by John Jason Jordan on 2022-08-30
I just did the dist-upgrade from 20.04.x to 22.04.1, which added the latest Subtitle Composer (0.7.1). Now it crashes every five or ten mintes, taking all your work with it. And when you open a sub/idx pair it instantly starts the OCR work, and there is no way to save your work as you go along. Just now I opened a sb/idx pair, got all the way to the end (an hour's work), and when I clicked to finish the OCR window disappeared and left me with nothing, no results at all, just an empty Subtitle Composer window waiting for me to open a file. 

There is no way to contact the developer, no support website or forums, nada.

---

### Post by tea for one on 2022-08-31
> **John Jason Jordan said:**
> There is no way to contact the developer, no support website or forums, nada.
Sometimes, you can find website info via synaptic.
Is this it [https://subtitlecomposer.kde.org/](https://subtitlecomposer.kde.org/)?

---

### Post by John Jason Jordan on 2022-08-31
> **tea for one said:**
> Sometimes, you can find website info via synaptic.
Is this it [https://subtitlecomposer.kde.org/](https://subtitlecomposer.kde.org/)?

Yeah, I finally found that link. But you have to sign up for a KDE account. No thanks. Add that Subtitle Composer is not very good. It doesn't use Tesseract for the OCR, and whatever it uses makes a lot of mistakes, so lots of time needed for the OCR, and then even more for cleanup. It needs more than just a bug report; it needs new developers to take it over.

Plus, the website that I mentioned earlier still has their suggestion of a $15 donation, but it's no longer a subscription, and it's no longer mandatory. Their work is superb; very few errors to clean up, and it takes only a couple minutes. So Subtitle Composer is no longer crucial. There are other websites too, but every other one I've tried fails to convert the idx/sub files when I upload them. Here's the link again: [https://subconverter.com/convert-sub-idx-to-srt-online/3fb5806b4119072d]("https://subconverter.com/convert-sub-idx-to-srt-online/3fb5806b4119072d")

There's also Subtitle Edit, but it's a Windows only program, although they offer instructions for Linux users to run it under Mono. Not my cup of tea.

---

### Post by John Jason Jordan on 2022-09-11
Well, [https://subconverter.com/convert-sub-idx-to-srt-online]("https://subconverter.com/convert-sub-idx-to-srt-online") has  gone back to requiring a monthly subscription with a Paypal auto-pay feature. They lowered the amount to $5, but it's the Paypal auto-pay feature that kills it for me. It's just about impossible to cancel a Paypal auto-pay - you have to file a complaint and go through a hearing. Been there, done that. No thanks.

---

### Post by Yellow Pasque on 2022-09-13
Maybe  you should try downloading this package and installing it with 'sudo dpkg -i': [http://deb-multimedia.org/pool/main/v/vobsub2srt-dmo/vobsub2srt_1.0~pre7+20171219-dmo3_amd64.deb](http://deb-multimedia.org/pool/main/v/vobsub2srt-dmo/vobsub2srt_1.0~pre7+20171219-dmo3_amd64.deb)

---

### Post by John Jason Jordan on 2022-09-13
> **Yellow Pasque said:**
> Maybe  you should try downloading this package and installing it with 'sudo dpkg -i': [http://deb-multimedia.org/pool/main/v/vobsub2srt-dmo/vobsub2srt_1.0~pre7+20171219-dmo3_amd64.deb](http://deb-multimedia.org/pool/main/v/vobsub2srt-dmo/vobsub2srt_1.0~pre7+20171219-dmo3_amd64.deb)

Hey, that looks really promising. Thanks! Only problem is I get an error: Dependency is not satisfiable: libtesseract5. I bet that means I need to install tesseract 5. I think I remember seeing a reference to it being available via a PPA. I'll poke around a bit; stay tuned!

Edit: I installed the tesseract PPA, which allowed me to install tesseract 5. But I still get

> Failed loading language 'eng'
Tesseract couldn't load any languages!
Failed to initialize tesseract (OCR).

Then I opened Synaptic and searched on 'tesseract,' which revealed that tesseract 4 was still installed. So I uninstalled tesseract 4, but I still get the same error messages. 

Failed loading language 'eng'
Tesseract couldn't load any languages!
Failed to initialize tesseract (OCR).

The maddening part is that all the traineddata file are right there in /usr/share/tesseract-ocr/, including in the subfolders - all 40 traineddata files. If only tesseract was human, then I could knock it up beside the head and make sure its eyes were working. Honestly, tesseract, the files are right *there*. See?

---

### Post by Yellow Pasque on 2022-09-14
Try:
```
vobsub2srt --tesseract-data /usr/share/tesseract-ocr/5/tessdata/
```

Other than that, I'm out of ideas. I can't really test it myself since I don't have any .idx/.sub files. Do you have a link to a sample?

---

### Post by John Jason Jordan on 2022-09-14
Your command suggestion gave me the same error messges as above, but the first time I tried it I got an additional error message: 'Please make sure the TESSDATA_PREFIX environment variable is set to the parent directory of your "tessdata" directory.' I've seen that error message before, and I tried to export an environment variable, but it won't take anything thatI've tried.

echo $TESSDATA_PREFIX
/usr/share/tesseract-ocr/4.00/
export $TESSDATA_PREFIX=/usr/share/tesseract-ocr/5/
bash: export: `/usr/share/tesseract-ocr/4.00/=/usr/share/tesseract-ocr/5/': not a valid identifier <What does that mean?>

OK, yesterday I found advice online to edit ~/.bashrc and add a line export TESSDATA_PREFIX='usr/share/tesseract-ocr/4.00/', followed by source ~/.bashrc, only it was before I upgraded tesseract to 5, so just now I edited the line by changing 4.00 to 5, then the source command again. And now echo $TESSDATA_PREFIX returns /usr/share/tesserct-ocr/5/. I also copied and pasted all 40 traineddata files into the /5/ folder. But tesseract still cannot find its data files. So then I did:

tesseract --list-langs
List of available languages in "usr/share/tesseract-ocr/5/" (0):
sudo tesseract --list-langs
<followed by all 40 languages>

OK, maybe ecerything has to be run as root. So I sudo-ed 'vobsub2srt filename', but still got the missing languages error messges. All I know for sure is that all 40 traineddata files are in the /5/ folder, and all are owned by root. So then I navigated the command line to /usr/share/tesseract-ocr/5/ and did 'sudo chown jjj:jjj *traineddata,' followed by a check on the properties of the files, and I now own them all. But 'tesseract --list-langs' still says there are -0- languages, and if I sudo the command I get all 40 languages. 

I'd be happy to post the sub/idx files somewhere, but I don't have accounts online for that. Where do people post files?

---

### Post by Yellow Pasque on 2022-09-15
> export: `/usr/share/tesseract-ocr/4.00/=/usr/share/tesseract-ocr/5/**'**: not a valid identifier <What does that mean?>
It looks like you used an apostophe (') instead of a backtick (`).

> Where do people post files? 
Google drive?

---

### Post by Yellow Pasque on 2022-09-15
In unrelated news, I pulled some old DVD's to try and get some .sub files and it appears I may need a new DVD drive. Sigh...

---

### Post by John Jason Jordan on 2022-09-16
I found that apparently I have an account at Google drive, and I uploaded filename.idx and filename.sub there. The URL is [https://drive.google.com/drive/quota]("https://drive.google.com/drive/quota") .

I don't know what a backtick is. It looks a bit like what the French call an accent grave. Do you know the Unicode value for it? And does it go at the beginning of the phrase, at the end, or both?

Re DVD drives, they're pretty cheap these days. Hopefully you can get the files I uploaded to Google drive so you won't need a new drive.

---

### Post by SeijiSensei on 2022-09-16
The "backtick" character ("`") has a special meaning in Unix. Any command inside of backticks will be run and its output sent to stdout. Nowadays that command has been deprecated in favor of $() for the same operation.

Quotation marks around file names should be either single-quotes (') or double-quotes ("). The former inteprets the material inside the quotes literally; it's a good option for lengthy file names with things like spaces and special characters. The double quote has a similar meaning, but it first substitutes the values of any Bash variables in the string. For instance,

```

STRING="Hello, world!"
echo '$STRING'
$STRING
echo "$STRING"
Hello, world!

```

The backtick appears on the key to the left of the numeral 1 on US keyboards.

---

### Post by Yellow Pasque on 2022-09-19
> **John Jason Jordan said:**
> The URL is [https://drive.google.com/drive/quota]("https://drive.google.com/drive/quota")

Sorry, but that's a generic link. It just takes me to my own Google Drive.

---

### Post by John Jason Jordan on 2022-09-20
> **Yellow Pasque said:**
> Sorry, but that's a generic link. It just takes me to my own Google Drive.

Sorry. I don't know how to give a link to my own Google Drive. Maybe there's asecret password or smething? Google is mostly beyond my ken.

But I finally broke down and installed Subtitle Edit. Over the years I have acquired various licenses for Windows when buying new computers, and I usually install them in Virtualbox, including Windows 10 from a couple years ago. Other than testing it after the install I have never launched it, but in frustration over not being able to OCR idx/sub files I finally did. I installed Subtitle Edit and then used it to convert the idx/sub files to an srt file, which I then moved back to my Ubuntu computer. I have some comments.

The link to the web site that I entered here above beats the pants off Subtitle Edit, (and I'd really like to know how they do it). You upload a sub and an idx file, it thinks about them for two or three minutes, and then you download the srt file. The srt file is 99% perfect; usually I need do nothing to it; it's ready to go. In contrast, with Subtitle Edit you watch for four or five minutes while it displays the OCR work as it progresses. You can see various errors that it makes, but you hope that at the end a spell checker will fix them. When you open the srt file your hopes are dashed. You must manually run the spell checker in a subtitle editor, and after trying half a dozen subtitle editors I can assure you that a normal subtitle srt file will take you one to two hours as you manually correct the errors. When I said 'spell checker' here everyone probably assumed that you clicked on a button to start it and then it automatically zoomed through the file in under a minute or two. That's not how it works in a subtitle editor. The spell checker stops on every single word in question and waits for your decision. It doesn't even remember your decisions; you have to type them back in each time the same error comes up. 

I should mention in passing that Subtitle Edit uses Tesseract. I am not impressed; and I should mention that the idx/sub files in question were from a Blu-ray disc at 1080p. Therefore, even if I can ever get vobsub2srt working here, the only advantage is in not having to run Windows; the results would likely be no better. And yes, I know you can run Subtitle Edit on Linux, but you have to install an interface, which is not my cup of tea.

Oh, and a slightly off-topic comment: I finally figured out why most DVDs and BDs come with VOBSUB subtitles. It's because television stations love them - they don't have to mess with fonts, and television stations send major checks to studios when they broadcast a movie.

---

### Post by Yellow Pasque on 2022-09-20
> Therefore, even if I can ever get vobsub2srt working here, the only advantage is in not having to run Windows; the results would likely be no better.

Bummer.. I was hoping we could make some kind of breakthrough with vobsub2srt. Maybe the problems with tesseract were the reason the devs seemingly abandoned it.

---

### Post by John Jason Jordan on 2022-09-21
> **Yellow Pasque said:**
> Bummer.. I was hoping we could make some kind of breakthrough with vobsub2srt. Maybe the problems with tesseract were the reason the devs seemingly abandoned it.

It occurs to me that Tesseract has the ability to save your personal experiences into one of the <lang>traineddata files - the files that here we continually failed to get Tesseract to find - yet Subtitle Edit offered no way to save my experiences with Tesseract. Now, I used it only for one sub/idx job, so I must add that it may have saved my changes, but without telling me that it was doing so. My point is that perhaps I am selling Tesseract a bit short; given better programming with additional use it might get much better. 

And one additional comment: The website mentioned previously that does such an incredible job, may be doing so because they have trained their OCR utility with thousands of sub/idx files that people have uploaded. And that leads me to a comment about Tesseract: Maybe it needs to be located only on the web, where it collects millions of user inputs. In the final analysis, OCR needs to be web based.

---

