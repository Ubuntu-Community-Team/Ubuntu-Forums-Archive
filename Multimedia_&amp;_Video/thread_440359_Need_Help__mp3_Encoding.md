---
title: "Need Help : mp3 Encoding"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by Prometheus.172214 on 2007-05-11
Hello Folks,
                    Being a newbie, I am kind of now in a position where I can use my Ubuntu notebook with ease (i.e. navigate menus and do mundane things). Here is a hitch. I am trying to use my existing collection of mp3 audio files which exist at different bit rates and would like to re-encode them as mp3 at 320kbps. The only software that I know of is Audacity and I am familiar with using this program in Windows, but not in Linux. I found the repository and have installed Audacity, but it needs the Lame Encoder to work. I downloaded the Lame tar.gz, but have no clue what so ever to compile. I am dunce at programming and compiling and so, I have no idea on how to proceed. Any help will be appreciated. If someone has a suggestion / program that will let me take existing mp3 audio files and re-encode them to a higher bitrate would be welcome. 

Thanks .....
:KS

---

### Post by stchman on 2007-05-11
> **Prometheus.172214 said:**
> Hello Folks,
                    Being a newbie, I am kind of now in a position where I can use my Ubuntu notebook with ease (i.e. navigate menus and do mundane things). Here is a hitch. I am trying to use my existing collection of mp3 audio files which exist at different bit rates and would like to re-encode them as mp3 at 320kbps. The only software that I know of is Audacity and I am familiar with using this program in Windows, but not in Linux. I found the repository and have installed Audacity, but it needs the Lame Encoder to work. I downloaded the Lame tar.gz, but have no clue what so ever to compile. I am dunce at programming and compiling and so, I have no idea on how to proceed. Any help will be appreciated. If someone has a suggestion / program that will let me take existing mp3 audio files and re-encode them to a higher bitrate would be welcome. 

Thanks .....
:KS

Follow my procedure.  LAME is part of the repository.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This will allow you to rip your existing CDs to mp3s.

Now as far as recoding mp3s to a lower bitrate try soundconvert

sudo apt-get install soundconvert

This package will allow you to recode mp3s from higher to lower 128Kbit size.  In the process apt-get will install all the dependencies.

Is sounds as though you want to convert your existing lower bitrate mp3s to a higher bitrate mp3?  That would be a complete waste of time.  Since whatever encoder you used encoded them at say 192Kbit then the information is already lost so don't bother.  You will need to re-rip your CDs.

---

### Post by Prometheus.172214 on 2007-05-11
First of all *w0oT* THANKS A TON ..... I am looking up the hyperlink you gave me......

Now, your response raises a question again and this one will probably make you feel like giving me a shakedown and that is because I am just starting with the encoding idea. So, you are saying that a file at lets say 128kbps ( a low bitrate I mean), if re-encoded to 320 would make no difference, because the quality is already compromised. Is that correct? Well, coming to re-ripping my audio collection, that will be a long task. I have abut 300 audio cds and the prospect of doing the entire exercise again is a bit ummm, errr, long ! I will try that anyway. I should have thought of this in the initial rip itself. I was conserving disc space at that time and now that I have more storage space, I don't mind the file size....

THANKS AGAIN....

:guitar:

---

### Post by stchman on 2007-05-11
> **Prometheus.172214 said:**
> First of all *w0oT* THANKS A TON ..... I am looking up the hyperlink you gave me......

Now, your response raises a question again and this one will probably make you feel like giving me a shakedown and that is because I am just starting with the encoding idea. So, you are saying that a file at lets say 128kbps ( a low bitrate I mean), if re-encoded to 320 would make no difference, because the quality is already compromised. Is that correct? Well, coming to re-ripping my audio collection, that will be a long task. I have abut 300 audio cds and the prospect of doing the entire exercise again is a bit ummm, errr, long ! I will try that anyway. I should have thought of this in the initial rip itself. I was conserving disc space at that time and now that I have more storage space, I don't mind the file size....

THANKS AGAIN....

:guitar:

Yes, mp3 is a lossy codec.  The lower the bitrate the more lossy it is.  I used to rip CDs at 128Kbs and found the sound was not as good as the CD.  I then started ripping CDs as 256Kbs and found the sound was FAR better on a nice system than 128Kbs.  I then discovered variable bitrate (VBR) and found that the sound was as good as 256Kbs and the file size was smaller.  That is because the LAME encoder analyzes the music and say during a period of silence the encoder determines that the bitrate can be real low while during loud complex passages the bitrate is upped.  The average bitrate for LAME is approx 200Kbs but sounds as good as the CD.

Since you music collection is 128Kbs the information is GONE.  Think of trying to make a VHS tape look as good as HD.  Cannot be done.

Rule of thumb for me that is.  CBR ripping should be done at minimum 256Kbs and use LAME whenever possible over CBR.

If you want better sound you can use OGG(lossy but better than mp3) or FLAC (losless).  These codecs have been researched superior to MP3, but their compatibility with many devices is poor.  Sound Juicer supports OGG and FLAC out of the box.  My procedure allows you to install MP3 ripping.  Let me know how it works for you.

---

### Post by Prometheus.172214 on 2007-05-11
Firstly, I will have to stay with mp3, because I use the same collection in my car. I have a 5 disc changer and being in a job where I travel long distances on car, I prefer to keep a big collection of music at hand. The car audio player that I have supports mp3, wma and Sony's atrac3. I have read somewhere that when compared with the latter options mp3 is a better option. Your answer points me into the right direction, I will re-rip my collection, but this time using a better bitrate (in vbr mode as you suggested). THANKS .... You just made my day........

:guitar:

---

### Post by stchman on 2007-05-11
> **Prometheus.172214 said:**
> Firstly, I will have to stay with mp3, because I use the same collection in my car. I have a 5 disc changer and being in a job where I travel long distances on car, I prefer to keep a big collection of music at hand. The car audio player that I have supports mp3, wma and Sony's atrac3. I have read somewhere that when compared with the latter options mp3 is a better option. Your answer points me into the right direction, I will re-rip my collection, but this time using a better bitrate (in vbr mode as you suggested). THANKS .... You just made my day........

:guitar:

Use VBR, but make sure your player supports it.  My car stereo plays mp3s in VBR for but to my surprise Windows Media Player needs a LAME plugin to support it.  Try a single VBR mp3 on a CD to see if it works.

---

### Post by Prometheus.172214 on 2007-05-11
I just tried two sample rips based on your idea....... The first one bombed and the audio ended up running as if in fast forward mode, no matter where I play it.... The second rip came out just fine and yes, I observe a notable improvement in terms of quality. Audio files that did not play that well before, play decently enough...... Now, for the tedious process of re-ripping my entire collection.......... 

B.T.W. : Windows Vista is a load on the system and needs some faster hardware to run smooth and I agree, it is kind of bloated in it's own way. But, I would say that it is a remarkable improvement from Microsoft, though a bit late.........

---

### Post by stchman on 2007-05-11
> **Prometheus.172214 said:**
> I just tried two sample rips based on your idea....... The first one bombed and the audio ended up running as if in fast forward mode, no matter where I play it.... The second rip came out just fine and yes, I observe a notable improvement in terms of quality. Audio files that did not play that well before, play decently enough...... Now, for the tedious process of re-ripping my entire collection.......... 

B.T.W. : Windows Vista is a load on the system and needs some faster hardware to run smooth and I agree, it is kind of bloated in it's own way. But, I would say that it is a remarkable improvement from Microsoft, though a bit late.........

Which one bombed or did you just re-try using the VBR method?  I find that the VBR will give you an excelletn copy of the song.  My ears cannot tell a difference.

---

### Post by Prometheus.172214 on 2007-07-04
Too late for the discussion, but never to late for an answer. Someone else may have the same problem and hence the answer, though very late.
my original rip collection was 128kbps and that was done to conserve disc space and mainly because, I wanted to carry a few discs with the songs and I had some albums, where I liked, just one song. 
The second time, I installed Audacity and Lame from the repository and ripped the discs again and this time, I select 256kpbs and there was a message on the screen with some information, which in a nutshell suggested additional ripping options. So, I did some more internet trawling and finally got the preferences configured in Audacity and it started ripping with variable bit rate. The first disc failed on all counts and I am suspecting a disc failure, because the second disc was perfect and yes, there was definitely an improvement in the audio experience.

---

