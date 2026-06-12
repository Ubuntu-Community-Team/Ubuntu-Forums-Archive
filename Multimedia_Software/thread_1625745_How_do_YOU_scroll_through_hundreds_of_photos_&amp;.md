---
title: "How do YOU scroll through hundreds of photos &amp; move good ones to a separate folder?"
date: 2010-11-19
forum: Multimedia Software
---

### Post by rocksockdoc on 2010-11-19
I'm relatively new to Ubuntu and am just trying to get basic functionality without having to punt back to Windows applications on Wine (such as Irfanview).

All I want to do is step through photos (by pressing a key, such as the space bar) to view & then press a keyclick to move the good ones to a separate folder. 

This is so fundamental that I must assume there must be software in Ubuntu which can accomplish those two simple tasks (step through a folder and move a file to another folder).

Yet, I have The Gimp, GNU Paint, Krita, KSnapshot, XFig, XPaint, etc., and none of them appear to have this basic functionality (which Irfanview has, but on Windows).

What program can view and easily MOVE the photo to a stated directory in a single keystroke?

Note: All the programs can "open a file" and "save as" but this is NOT the desired fundamental operation. The fundamental operation is:
- Press a key (spacebar would be nice) to scroll to the next photo in a folder
- Press another key combination ("control + m" would be nice) to move the photo to a stated folder
- The "index" should NOT be reset (that is, the next spacebar should show the next photograph in the folder, not jump back, perhaps hundreds of photos, to the first photo as The Gimp does, for example, after a save).
- It's ok to set the move-to folder the first time, but it should not ask each and every time which folder as it should be the default for the move command after the first move.

Note: I also tried making the icons in the Nautilus browser huge and then control-click selecting the good ones, but that makes ALL icons at all times huge, and the scroll in Nautilus is atrocious, so, in effect, that was a failure. I need a graphic program that performs this simple task.

This is so fundamental of a need (to scroll through and move just the good photos to a stated folder) that I find it hard to believe I can't (yet) find a graphics display program capable of scrolling and moving photos. 

[SIZE=3]**[COLOR=DarkRed]How do YOU scroll through hundreds of photos to move the good ones to a separate folder?[/COLOR]**[/SIZE]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175988&stc=1&d=1290188575[/IMG]

---

### Post by endotherm on 2010-11-19
there are several image viewers that support extensible (custom) commands. Geequie and mirage are a couple of these. 

you can set up a custom command/Action like this:
cp %f /data/archive/goodpics
or whatever else you might want. then when you come to a good pic, just execute teh command (in mirage they are called "Custom Actions" ;  Edit -> Custom Actions ) to move or copy the file.

---

### Post by naviathan on 2010-11-19
> **endotherm said:**
> there are several image viewers that support extensible (custom) commands. Geeqie and mirage are a couple of these. 
 
then set up a custom command with somthing like:
cp %f /data/archive/gioodpics
or whatever else you might want. then when you come to a good pic, just execute teh command (in mirage they are called "Custom Actions" ; Edit -> Custom Actions ) to move or copy the file.
 
I like that solution.  I've been wondering about this one myself.

---

### Post by nothingspecial on 2010-11-19
You need feh

```
sudo apt-get install feh
```

Then ```
feh -rF -D 3 ~/Photos
```

That command initiates a slideshow of your photos. You will have to change ~/Photos to the directory your photos reside in.

I`ll break the command down for you.

-r means recursive in that you only have to specify the parent directory, it will go through all the sub directories aswell

-F means fullscreen

-D 3 means show each photo for 3 seconds before moving to the next one, change the 3 for whatever you like.

Now.......

right arrow (->) will go to the next image
left arrow (<-) will go back
H will pause (if you need a beer)

And this is the important bit........

F will save the photo you are veiwing to the directory you started feh in

So........

I`m going to assume your photos are at ~/Photos  .........

Make a folder for the good ones

```
mkdir ~/good_pics
```

Go there

```
cd ~/good_pics
```

Start the slideshow
```

feh -rF -D 3 ~/Photos
```

If you don`t like one, press -> to go to the next one

If you like one, press F

If you miss saving one, go back with <-

After you`re done, all your good ones will be in ~/good_pics

---

### Post by rocksockdoc on 2010-11-19
> **nothingspecial said:**
> ... press -> to go to the next one
... If you like one, press F ... go back with <- ...all your good ones will be in ~/good_pics

That's EXACTLY the operation I want!
- I want to scroll forward (or backward) at my own speed (> or <)
- For any picture I like, Ill press "F"
- In the end, all the good ones are in ~/path/good_pic

Perfect use model. 

I'll install and check it out and report back how it goes!

Thanks (I can see I wasn't the first to ask this question!)

---

### Post by rocksockdoc on 2010-11-19
Here's what I did, assuming photos in /path/photos:
```

mkdir /path/photos/best
cd !$
feh -F  ..

```This quickly (muuuuch quicker than Gimp, for example) brought up the first picture in fullscreen mode (-F) and only scrolled forward when I pressed a key ("spacebar") or scrolled backward when I pressed a key ("backspace") just like Irfanview does on Windows. 

Just like Irfanview, hitting escape ("Esc") gracefully exited out of the program.

The only problem was "F" saved a text file which looked like a directory listing, of the name "feh_021461_000001_filelist", so it must be some other key that moves a file. I hit every key ("m", for example, brings up a menu); but I haven't hit upon which key does the move into the current directory.

Am I doing something wrong?

---

### Post by rocksockdoc on 2010-11-19
While the "feh" slideshow keys "spacebar" & "backspace" scroll through the photos in the folder, and "esc" will exit the program, the only thing left is the "move" or "copy" slideshow command. 

I see from the "feh" manpages that the "f" or "F" slideshow key is not what we need:
```

f, F Save the current filelist to a unique filename.

```But, the "save" slideshow key seems to (silently) do the trick:
```

s, S Save the current image to a unique filename.

```So, here's the use model:
```

a) Given a directory of photos, e.g., /media/Flash Drive/pictures
b) Create a sub directory to hold files, e.g., mkdir "/media/Flash Drive/pictures/save"
c) Go to that sub directory, e.g., cd !$
d) Run "feh" in any desired mode, e.g., "feh .." or "feh -F .."
e) Use the "spacebar" to step forward through the picture set
f) Use the "backspace" key to step backward through the picture set
g) Use the "S" (or "s") key to silently copy the file to the current directory
h) Use the "Esc" key to escape out of the program

```This is fast (much faster than any other editing program on Ubuntu to date), intuitive (works almost the same as Irfanview, the admitted leader in simple photo manipulation), and easy.

Thanks for the help! I hope others benefit if they find this in their google searches.

---

### Post by rocksockdoc on 2010-11-19
So, here's my use model (please improve if you have better ideas) to email out a bunch of pictures to family and friends.

1. Snap a few hundred photos & copy to a hard disk (e.g., to /media/My Disk/pics)
2. Batch rotate the photos according to EXIF orientation tags (e.g., exiftran -ai *.JPG)
3. Create a directory for a shrunken mailable copy (e.g., mkdir /media/"My Disk"/pics/small)
4. Copy the entire set of large photos to that new directory
5. Batch shrink the photos to an emailable 640x480 pixels (e.g., find . -iname "*.jpg" -exec convert -resize 640x480 -quality 86 -strip {};) or use Nautilus to right-click resize to 640x480 pixels.
6. Create a directory to hold the best photos to be emailed (e.g., /media/"My Disk"/pics/best)
7. Go to that (currently empty) best-photo directory (e.g., cd /media/"My Disk"/pics/best)
8. View the desired pictures (e.g., feh -F ..)
9. In feh slideshow mode, use "spacebar" and "backspace" to navigate forward and backward through the photo set
10. In feh slideshow mode, use the "s" key to save a copy of the good pictures to the current directory
11. Hit the "Escape" key to exit out of 'feh' slideshow mode
12. Email just these, the best of the photographs in your set.

If you have an improvement to this process, please suggest it so we all benefit.

---

### Post by nothingspecial on 2010-11-20
Glad I could be of help.

Your needs with feh, go beyond mine.

I use it for 2 things. One as I've outlined. When we (me, wife and kids) come back from a holiday for example, we do what I said in my earlier post. We do the slide show, and if someone wants that picture, they shout and I hit F.

After were done, I send them to the printing company.

The other thing is to use it on a broken netbook I have as a digital photo frame, with the -z option for random.

I often find that cli apps can be more intuitive and useful than their gui counterparts.

feh also has one of the best written man pages I have seen.

---

### Post by rocksockdoc on 2010-11-21
> **nothingspecial said:**
> Glad I could be of help.

Yup. The only problem with "feh" was that typing the path was onerous, especially with spaces being in my media disk drive auto-assigned names; but I think I'll install "nautilus-open-terminal" to solve that problem. Once installed, I'm told I can just right click to open a terminal window to run "feh" in the desired directory.

What I'm looking up next is how to automatically rename the photo files based on the EXIF date they were taken.

---

### Post by nothingspecial on 2010-11-22
You can drag a directory into gnome-terminal.

So type cd, then drag the directory into the terminal and you will be there after you hit enter.

Also, you can use tab completion -

eg if you have a directory```
 ~/Photos/My\ Daughters\ 3rd\ Birthday\ Party
```Just type

```
feh -options ~/Ph
```then hit Tab

You will get

```
feh -options ~/Photos
```Type My 

so you get


```
feh -options ~/Photos/My
```then hit Tab again which should give you the whole path

 ```
~/Photos/ My\ Daughters\ 3rd\ Birthday\ Party
```Also, the bash shorthand for the current directory is . (a full stop/period)

So if you are in the directory you want to be in, having dragged it into the terminal, you can type

```
feh -options .
```If you have a lot of these directories you want to go through, and you are going to spend some time on this, then put an alias in your .bashrc. 

```
gedit ~/.bashrc
```Put a line like this at the end
```

alias slide='feh -rzF -D 3 ./'
```Save, close, then type```
 . ~/.bashrc
```From now on, if you are in the directory you want to view, just type ```
slide
```

---

### Post by rocksockdoc on 2010-12-04
> **nothingspecial said:**
> ```
feh -options ~/Photos
```

I've been using "feh" daily and I just love it. It's not user friendly without the nautilus terminal, but, with nautilus terminal, there's no problem opening up a terminal window in the directory of the photos.

In a sub directory of the photos, to move the ones I like best, here's what I do now:

```

1st, navigate to the photo folder in the Gnome GUI
2nd, I create a sub-folder, e.g., "bestpics"
3rd, I navigate to that bestpics folder & right click to "Open in terminal" 
4th, at the prompt, I type:  $ feh -F -A "mv %f ./%n" ..

```

What this does is show the photos in the directory just above (..) in full-screen mode (-F) as I hit the "space" bar to navigate through the photo set. When I see a great picture, I simply hit the "enter" key, which then executes the action (A) which, in this case, is to run the command "mv %f ./%n". 

That moves the selected file (%f) to the current directory (./) and keeps the same file name "%f" as it was prior. 

I just love simple solutions to common problems!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177429&stc=1&d=1291523874[/IMG]

---

### Post by rocksockdoc on 2011-04-29
For the record, curbuntuforums provided a great syntactic hint for operating on photos on the fly over here:
- [**Is there an extension to "Eye of Gnome" to RENAME or DELETE pictures while viewing?**]("http://ubuntuforums.org/showthread.php?t=1737710")

```

$ feh *.jpg --action1 "rm %f" --action2 "mv %f ./good/." --action3 "cp %f ./good/.; mv %f ./bad/"

```Using that command, while viewing the file in Feh, pressing the "1" keyboard key will delete the file; pressing the "2" button will move the file to the "good" folder; and pressing the "3" button will both copy the file and move it.

Nice!

In addition, in Feh, "control delete" also deletes the file.

We're not sure how to rename files on the fly, but a clever script might somehow take keyboard input ...

---

