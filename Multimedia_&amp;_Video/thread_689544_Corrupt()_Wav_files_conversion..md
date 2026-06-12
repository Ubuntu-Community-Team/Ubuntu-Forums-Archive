---
title: "Corrupt(?) Wav files conversion."
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by zasdarq on 2008-02-06
Hello,

I'm attempting to encode fairly large WAV files (90 - 800 MB each) to FLAC files using the flactools. The files play fine while in wave format, and I've been able to encode some test waves to flac and play those flac files as well.  However, when converting this group of WAV files to FLAC, the FLAC will not open after the encoding.  Errors:

Default Player: "An Error Occurred: Could Not Decode Stream"
flac123: "error handler called!" <- repeated over and over and over
VLC: no error, it "plays" but the timer isn't at 00:00:00 the whole time and no sound

There are no errors during the encoding, though there are some warnings.
Here is the output:

flac -f -8 --verify 10_A.wav

10_A.wav: WARNING: skipping unknown sub-chunk 'bext' (use
--keep-foreign-metadata to keep)
10_A.wav: WARNING: legacy WAVE file has format type 1 but bits-per-sample=24
10_A.wav: WARNING: skipping unknown sub-chunk 'minf' (use
--keep-foreign-metadata to keep)
10_A.wav: WARNING: skipping unknown sub-chunk 'elm1' (use
--keep-foreign-metadata to keep)
10_A.wav: 100% complete, ratio=0.62410_A.wav: WARNING: skipping unknown
sub-chunk 'regn' (use --keep-foreign-metadata to keep)
10_A.wav: WARNING: skipping unknown sub-chunk 'ovwf' (use
--keep-foreign-metadata to keep)
10_A.wav: WARNING: skipping unknown sub-chunk 'umid' (use
--keep-foreign-metadata to keep)
10_A.wav: Verify OK, wrote 168060055 bytes, ratio=0.624


As a final random test, I attempted to split one of the wav files using wavsplit.  That resulted in the following output/error.

Channels: 1
Samplerate: 96000Hz
Samplebits: 24
Databytes: 269503836

Split         Hours  Mins   Seconds         Bytes         %
Bad file format

I also attempted to convert the WAVE files to MP3 using lame... the same problem arises where I cannot play the resulting MP3 file but there are no errors during the encoding.

Could this be a problem with the codecs for FLAC?  Since I can play other files, I don't believe that's it.  My best guess is that something is wrong with the wav files, but I don' know how to go about checking them. Is there an integrity checker app or something?  I'm fairly new in the audio format world so I'm lost on most of it.  

Thank you for the help! Sorry for the long post, I tried to be as detailed as possible.
Matthew

---

### Post by ron999 on 2008-02-06
I have had similar problems with WAV files.
When it happens I import the WAV file into Audacity.
Then I export it again as WAV, but make sure that in Preferences > Uncompressed Export Format > WAV (Microsoft 16 bit PCM) is set.
Maybe there's an easier way.

---

### Post by zasdarq on 2008-02-06
Interesting, that also worked for me.  Flac doesn't support 32 bit float/integer wav files... so perhaps thats the problem.  Converting it to a 16 bit file is bound to result in loss of information, no?  I'm fairly new at the whole audio thing.

Is there a faster way to do these conversions than Audacity?  I'm writing a program to batch process hundreds of these files so importing and exporting each by hand isn't an option.

How can I check the current type of wav file I have (it's bits and sample rate?)

Thanks,
Matthew

---

