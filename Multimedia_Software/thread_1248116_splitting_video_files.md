---
title: "splitting video files"
date: 2009-08-23
forum: Multimedia Software
---

### Post by tonymoloney on 2009-08-23
I have been asked to edit a 1.03GB video file of a live band performance.
The video was taken on a Sony Handycam with an internal miniDVD disc and is in .VRO format.
I tried using Lives for the job, and it looks like this will be the way to go, but my problem is my computer has only 1GB of memory.
Is there any way in which I could split the original file into, say, 100MB chunks, edit each chunk, then recombine the results?
I am thinking along the lines of splitting movie.vro into part1.vro, part2.vro, part3.vro... then producing newpart1.vro etc, then finally combining the new parts into final.vro
In the good old days of DOS, this sort of thing was possible, but in those days, files were just data and didn't carry all sorts of embedded formatting information like they do now.
This looks like a job for the terminal and I don't mind going down that path.
Tony

---

### Post by tonymoloney on 2009-08-23
Well, it looks like I've solved my own problem.
Searching around the Ubuntu Wiki lead me to a page that showed how to split files.
It took a lot of experimenting to get the size right, but eventually the command <split --bytes=102400000 movie.vro> got the job done.
I then tested several of the output files to make sure that they still played and didn't lose any sound
It was then able to delete the first few blocks and recombine the files with a simple <cat> command
Job done!
Tony

---

