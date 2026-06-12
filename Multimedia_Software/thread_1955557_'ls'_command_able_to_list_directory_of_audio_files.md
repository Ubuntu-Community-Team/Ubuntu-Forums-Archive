---
title: "'ls' command able to list directory of audio files bitrates too?"
date: 2012-04-09
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-09
Is it possible for the 'ls' command to list a directory of audio files and display their bitrates as well?

so far here's what's worked for me:

```
ls -C -R -s >file-contents.nfo
```

Is there a way I can make it display the bitrates?

---

### Post by Toz on 2012-04-09
I don't believe ls can do that, but if you use the file command, you can get that information. Something like this:
```
for f in *.mp3; do echo `ls -C -R -s "$f"` \(`file "$f" | cut -d',' -f5` \); done
```

Probably best to assign it to an alias:
```
alias bls='for f in *.mp3; do echo `ls -C -R -s "$f"` \(`file "$f" | cut -d',' -f5` \); done'
```

---

### Post by AlexOnVinyl on 2012-04-09
> **Toz said:**
> I don't believe ls can do that, but if you use the file command, you can get that information. Something like this:
```
for f in *.mp3; do echo `ls -C -R -s "$f"` \(`file "$f" | cut -d',' -f5` \); done
```

Probably best to assign it to an alias:
```
alias bls='for f in *.mp3; do echo `ls -C -R -s "$f"` \(`file "$f" | cut -d',' -f5` \); done'
```


can you explain exactly what I'm putting in? I'm a little confused.. :frown:

---

### Post by Toz on 2012-04-10
Sure.

```
for f in *.mp3;
```
...for every mp3 file in the current directory...

```
do
```
...do the following...

```
echo `ls -C -R -s "$f"`
```
...this is your existing code to list the files by columns (-C), recursively (-R), and print its size in blocks (-s)...

```
\(`file "$f" | cut -d',' -f5` \);
```
...and append to each entry the bitrate as obtained using the file command (the bitrate is in the 5th comma-separated column)...

```
done
```
...done...

The $f is a placeholder for every mp3 file in the directory - it is replaced by the name of each file it finds as it works through the directory.

---

### Post by AlexOnVinyl on 2012-04-11
> **Toz said:**
> Sure.

```
for f in *.mp3;
```
...for every mp3 file in the current directory...

```
do
```
...do the following...

```
echo `ls -C -R -s "$f"`
```
...this is your existing code to list the files by columns (-C), recursively (-R), and print its size in blocks (-s)...

```
\(`file "$f" | cut -d',' -f5` \);
```
...and append to each entry the bitrate as obtained using the file command (the bitrate is in the 5th comma-separated column)...

```
done
```
...done...

The $f is a placeholder for every mp3 file in the directory - it is replaced by the name of each file it finds as it works through the directory.

So basically - everything that you have wrapped in the CODE boxes is what I put in?

---

### Post by nothingspecial on 2012-04-11
You could use sox

```
sudo apt-get install sox libsox-fmt-all
```

Then when you are in the directory with the music type

```
soxi *
```

---

### Post by Toz on 2012-04-11
> **AlexOnVinyl said:**
> So basically - everything that you have wrapped in the CODE boxes is what I put in?

Yes, the first box if you want to just type it into the terminal. You'll find this tedious. The better option is to add the contents of the second box to your ~/.bashrc file. Close and open a new terminal and then just type in **bls** when in a directory to run the longer command.

---

### Post by AlexOnVinyl on 2012-04-12
> **nothingspecial said:**
> You could use sox

```
sudo apt-get install sox libsox-fmt-all
```

Then when you are in the directory with the music type

```
soxi *
```

> **Toz said:**
> Yes, the first box if you want to just type it into the terminal. You'll find this tedious. The better option is to add the contents of the second box to your ~/.bashrc file. Close and open a new terminal and then just type in **bls** when in a directory to run the longer command.

Thanks guys I'll report back with my outcomes

---

### Post by AlexOnVinyl on 2012-04-12
> **nothingspecial said:**
> You could use sox

```
sudo apt-get install sox libsox-fmt-all
```

Then when you are in the directory with the music type

```
soxi *
```

I installed sox - then made this script:

```
#!/bin/bash

soxi * >file-info.nfo && soxi * >file-info.log
```

Is there any way I can set it to go through each subfolder and subdirectory and list the files - that way if I have a lot of folders with music files in them I want indexed, it will just go through automatically?

---

### Post by enkay009 on 2012-04-12
> **AlexOnVinyl said:**
> I installed sox - then made this script:

```
#!/bin/bash

soxi * >file-info.nfo && soxi * >file-info.log
```

Is there any way I can set it to go through each subfolder and subdirectory and list the files - that way if I have a lot of folders with music files in them I want indexed, it will just go through automatically?

You could run find and specify an execute option. 

```
find /path/to/my/mp3/directory -type f -exec soxi {} \; > file-info.log
```

This will recursively return all files ( -type f ) under your path ( /path/to/my/mp3/directory ) and run a command on them ( -exec soxi {} \; ).

You can be a even be more precise and specify a file pattern.

```
find /path/to/my/mp3/directory -type f -name '*.mp3' -exec soxi {} \;
```

---

### Post by nothingspecial on 2012-04-12
Just to be pedantic :p

With find, in this case,  you are much better to specify -name before -type f

find finds everything then checks your specifications one by one left to right so if you specify -type f first it will find every single file and then check if they are called *.mp3

If you put -name first it will only check if anything called *.mp3 is a file before continuing.

Makes no difference if you don't have a lot of music, but if your collection is anything like mine, with 10s of thousands of flac files and very few mp3s, it would.

---

### Post by AlexOnVinyl on 2012-04-13
> **nothingspecial said:**
> Just to be pedantic :p

With find, in this case,  you are much better to specify -name before -type f

find finds everything then checks your specifications one by one left to right so if you specify -type f first it will find every single file and then check if they are called *.mp3

If you put -name first it will only check if anything called *.mp3 is a file before continuing.

Makes no difference if you don't have a lot of music, but if your collection is anything like mine, with 10s of thousands of flac files and very few mp3s, it would.

hahah I'll look into it. 

> **enkay009 said:**
> You could run find and specify an execute option. 

```
find /path/to/my/mp3/directory -type f -exec soxi {} \; > file-info.log
```

This will recursively return all files ( -type f ) under your path ( /path/to/my/mp3/directory ) and run a command on them ( -exec soxi {} \; ).

You can be a even be more precise and specify a file pattern.

```
find /path/to/my/mp3/directory -type f -name '*.mp3' -exec soxi {} \;
```

Could you go into detail what the ```
{} \;
``` stand for individually please? as I said I'm just learning to script with Bash.  And just started ubuntu in August :) quite satisfied with Linux over any other OS.

---

### Post by nothingspecial on 2012-04-13
> **AlexOnVinyl said:**
> 



Could you go into detail what the ```
{} \;
``` stand for individually please? as I said I'm just learning to script with Bash.  And just started ubuntu in August :) quite satisfied with Linux over any other OS.


{} means what find has found

\; ends the find command

---

### Post by AlexOnVinyl on 2012-04-16
> **nothingspecial said:**
> {} means what find has found

\; ends the find command

how can I take this: ```
find /path/to/my/mp3/directory -type f -name '*.mp3' -exec soxi {} \;
```

and change the ```
/path/to/my/mp3/directory
``` to work with whatever I want it to be when I run the script - as in to work with Nautilus.  As like if I wanted to right click on the folder and have it run on that specific folder?

---

### Post by nothingspecial on 2012-04-16
Well I've never had a look at nautilus scripts so I am unsure how they work but ./ expands to the current working directory so

```
find ./ -type f -name '*.mp3' -exec soxi {} \;
```

---

### Post by AlexOnVinyl on 2012-04-17
> **nothingspecial said:**
> Well I've never had a look at nautilus scripts so I am unsure how they work but ./ expands to the current working directory so

```
find ./ -type f -name '*.mp3' -exec soxi {} \;
```


Lol we could both be learning something here.  And no, not Nautilus - I mean Im making a bash script to put into the ~/.gnome2/nautilus-scripts/ folder to use it as a script - like a 1 click terminal command

---

