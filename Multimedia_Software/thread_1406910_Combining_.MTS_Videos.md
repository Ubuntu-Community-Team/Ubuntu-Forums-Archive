---
title: "Combining .MTS Videos"
date: 2010-02-14
forum: Multimedia Software
---

### Post by TheropodWatcher on 2010-02-14
I've been trying for some time to find a tool that would let me take several .MTS scenes from my Vixia video camera and combine them into one video. I wanted to do this without down-grading the resolution if at all possible. I haven't been able to find anything that would do the job right - but I did come up with a trick to get it done, and hope this may help others using .MTS files.

In a shell you can actualy cat the files together. Type something like:
cat firstfile.MTS secondfile.MTS thirdfile.MTS > combinedfilename.MTS

Who'd have "thunk" it - it works! Sort of. I could not play the resulting combined file all the way through with vlc unfortunately (this is hit-or-miss, works sometimes). But I could convert it into a .m4v using HandBrake. For now that does it for me. Now to figure out a way to add a title video at the beginning ...

An example made from three separate .MTS files is at this URL:
[http://www.youtube.com/watch?v=GVnnuHmBl0Q](http://www.youtube.com/watch?v=GVnnuHmBl0Q)

Hope this is of some use to someone. 
Note: I don't get on the forums often. You can contact me at Brad at Theropod dot org if you have any questions, but this is actually pretty darn simple if you play with it a bit.

---

### Post by c10273 on 2010-02-14
I have that problem also. I recently bought a vixia camcorder. I am a total noob and I don't understand how to shell the files together. I was wondering if you could explain a little more of how I can do that. Thank you in advance.

---

### Post by TheropodWatcher on 2010-02-14
OKay, not knowing how much you know, I'm not insulting you, just trying to be thorough.

Open a shell (pull-down menus Applications>Accessories>Terminal). Use the cd command to enter the directory where your videos are stored (e.g., cd Videos). You can use the pwd command to see where you are in the directory tree (you'll start in your home directory) if you need to ("present working directory"), and the ls command ("list") to see what's in the directory. Use ls -l ("list -long") for more information about the directory items such as size, which are files and which are sub-directories, etc. A sub-directory will be indicated by the letter d in the far left column of the listing. Videos in our example would be a sub-directory off our home directory.

Once you find your videos, decide which ones you want to combine. Example 0001.MTS, 0006.MTS, 0011.MTS - whatever they are. Use the cat command to combine them. You enter the names into the command in the order in which you want the files to appear in the final video. Then you add a redirect symbol > and finally a filename for the video you want to create. So if we want to see them in the order we took them in a video we'll call MyVideo this is the command:

cat 0001.MTS 0006.MTS 0011.MTS > MyVideo.MTS

Remember that command line work is case sensitive. So MTS has to be MTS, not mts and so on. Press return. When the command prompt returns, you'll have your combined .MTS file, in this case named MyVideo.MTS.

Close the shell (terminal). You don't need it any longer. You can either click the close window gadget or type exit and press return.

At this point, bring up HandBrake, load your combined video into it and convert in the normal way. The HandBrake documentation should tell you all you need to get that part done. 

It might go something like this

mycomputername:~$ ls {press Enter / Return}
Desktop             Documents         Software
FileShare           Photos            Temp
Templates           Pictures          Videos

mycomputername:~$ cd Videos
mycomputername:~/Videos$ ls
0001.MTS           0002.MTS           0003.MTS
0004.MTS           0006.MTS           0008.MTS
0009.MTS           0011.MTS
mycomputername:~/Videos$ cat 0001.MTS 0006.MTS 0011.MTS > MyVideo.MTS
mycomputername:~/Videos$ ls
0001.MTS           0002.MTS           0003.MTS
0004.MTS           0006.MTS           0008.MTS
0009.MTS           0011.MTS           MyVideo.MTS
mycomputername:~/Videos$ exit

And off to HandBrake

If you have your videos in sub-directories, you'd use cd to get to the right sub-directory then proceed as shown.


Let me know if I went too lightly over anything.
 Regards,
 Brad

---

### Post by c10273 on 2010-02-27
Thank you so much for that info. It worked seamlessly, didn't notice a thing when merging the video back together. I wasn't able to view it on the computer itself. I had to transfer to my home server and view it on the PS3. I tried merging with kdenlive and openshot but the computer was not powerful enough. This way doesn't hardly blink an eye. It took a little while for me to get around to try it. Again thank you!

---

