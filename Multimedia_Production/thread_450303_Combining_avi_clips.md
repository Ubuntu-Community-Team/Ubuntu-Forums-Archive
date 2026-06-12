---
title: "Combining avi clips"
date: 2007-05-21
forum: Multimedia Production
---

### Post by Lucretia on 2007-05-21
I have three avi clips that I want to combine. I don't want to do any other editing.

I tried Avidemux, but it didn't work. It seemed to combine them, but when I try to play the clip in Totem, it doesn't. There is no sound and if I push play, nothing happens. The original files were mov and I converted them to avi using Mencoder.

Kino won't load my files, and Cinelerra is too complex for what I want to do.

Does anyone have any suggestions? Even just a command line program is fine.

---

### Post by jiminycricket on 2007-05-23
Hi Lucretia,
this seems to have a command line solution: [http://ubuntuforums.org/archive/index.php/t-85718.html](http://ubuntuforums.org/archive/index.php/t-85718.html)

> fleshnblood
November 3rd, 2005, 11:02 AM
To join separate mpeg files (for example a movie) into one smooth mpeg file:
cat file1.mpg file2.mpg file3.mpg... > filename.mpg
Pay attention to the order of files after the cat command, it will determine the sequence within the final file.
This will ONLY join the files! It has NO EFFECT on the quality.
It DOES NOT work with AVI files!
poptones
November 3rd, 2005, 11:44 AM
Actually, it does work with avi files or ANY files split with something like hjsplit.

It will also work on ANY AVI files so long as you have mplayer installed. After joining some arbritrary group of AVI files via "cat," tell mplayer to rebuild the index

mencoder -forceidx -oac copy -ovc copy infile.avi -o outfile.avi
fleshnblood
November 3rd, 2005, 12:00 PM
Actually, it does work with avi files or ANY files split with something like hjsplit.

It will also work on ANY AVI files so long as you have mplayer installed. After joining some arbritrary group of AVI files via "cat," tell mplayer to rebuild the index

mencoder -forceidx -oac copy -ovc copy infile.avi -o outfile.avi

Thanks for the tip, I haven't tried it through mplayer. When I joined AVI files with cat, the final file was OK in terms of picture but the audio was shifted. So I guess mplayer fine-tunes it, right?

---

### Post by justin13 on 2007-06-01
[http://www.arsgeek.com/?p=435](http://www.arsgeek.com/?p=435) is another good site:



I have recently started watching the fab serialized movie Bloodspell, which is created entirely in Neverwinter Nights.

Bloodspell is released in a series of 6-7 MB files. So far they’re up to part 7. This certainly makes it easier to download on to my laptop and enjoy 10 minutes of Bloodspell at a time. However, I want to burn this to a DVD and watch all seven at once on my home DVD player. Before I did this I just wanted to string together the 7 .avi files into one larger file. (I can’t stand a mess!) Sounds like a simple request? Guess what, in my distro, Ubuntu, it is!

This will most likely work on just about any linux distro that includes the ability to install mplayer/mencoder.

First, let’s get the right programs.

    sudo apt-get install mencoder mplayer

Now that the hard part is out of the way, we’re going to make use of the wonderful cat command. I’d renamed each Bloodspell video as b1.avi - b7.avi. Now to string them all end to end.

    cat b1.avi b2.avi b3.avi b4.avi b5.avi b6.avi b7.avi > bloodspell.avi

Now we’re 2/3 of the way there! Stringing together .avi files can cause a breakdown in the sync between video and sound. So, we’ll use mencoder to sort things out.

    mencoder -forceidx -oac copy -ovc copy bloodspell.avi.avi -o bloodspell_final.avi

That’s it! You’ve got one contiguous .avi file now containing all seven bloodspell releases to date. This will of course work with other .avi files. It will also work with .mpg or .mpeg files as well.

have tried this and tested and it came out perfect :)

---

