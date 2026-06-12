---
title: "Batch-processing of projects in avidemux"
date: 2013-06-07
forum: Multimedia Software
---

### Post by whocares02 on 2013-06-07
Hi,
just found [this threat]("http://ubuntuforums.org/showthread.php?t=1839503") about batch-processing files with avidemux. 
My question: Is there a way to batch-process .proj-files?

I have a big folder full of TV-recordings which need to get cutted and encoded afterwards. I wanna do all the cutting-stuff in a 2-hours-session to create a bunch of .proj-files.
In a second step they all shall be encoded one after another automatically, so I just let the computer run for a day or two. Not sure if batch-processing two encoding jobs at the same time would be more efficient though (CPU has 4 cores).

However, is there a way to do such a project-queue by script? Or is there something alike already built-in?

Thanks in advance for help.

---

### Post by whocares02 on 2013-06-07
First answer I can giv myself: [This website]("http://whirlpool.net.au/wiki/avidemux") says it **is** possible and uses this script:

```
tcsh% touch donelist.txt
tcsh% foreach i (`ls *.proj | cut -d'.' -f1`)
> echo $i >> donelist.txt
> avidemux2 --load ${i}.proj --save ${i}.svcd.mpg --quit
> end
```

I can see that they are not using a typical bash-script. So with my poor scripting-knowledge I tried rewriting it:


```
#!/bin/bash

touch donelist.txt
foreach i in (`ls *.proj | cut -d'.' -f1`) ; do
  echo $i >> donelist.txt
  avidemux2 --load ${i}.proj --save ${i}.mkv --quit
end

```

 Would this script work fine? I'm not sure with syntax of the foreach-loop. How would I do a batch-script processing two jobs at the same time?

In addition, I found [this]("http://www.avidemux.org/admWiki/doku.php?id=using:project_files") wiki-page telling something about "Jobs":

> Jobs are in fact also ECMAScripts. They only differ from a regular project file by an additionnal &#8220;app.save(filename);&#8221; line at the end. They are stored in $HOME/.avidemux/jobs/ directory.

Is there a simple way to execute two of such jobs at the same time and in a batch-queue? Maybe this was easier than bash-scripting.

---

### Post by whocares02 on 2013-06-07
Nobody?

---

### Post by ferdnyc on 2013-08-17
> **whocares02 said:**
> I can see that they are not using a typical bash-script. So with my poor scripting-knowledge I tried rewriting it:

```
#!/bin/bash

touch donelist.txt
foreach i in (`ls *.proj | cut -d'.' -f1`) ; do
  echo $i >> donelist.txt
  avidemux2 --load ${i}.proj --save ${i}.mkv --quit
end

```

 Would this script work fine? I'm not sure with syntax of the foreach-loop. How would I do a batch-script processing two jobs at the same time?

Is there a simple way to execute two of such jobs at the same time and in a batch-queue? Maybe this was easier than bash-scripting.

There are plenty of ways to manage parallel jobs on the command line, but one of the better and more robust (without being needlessly complicated for this fairly simple task) is [GNU Parallel]("http://www.gnu.org/software/parallel/"). I'm sure it's available in Ubuntu, tho I can't offer specifics as I'm a Fedora user.

Parallel has an excellent manpage, but translating the code above into its clever syntax is pretty trivial. It would simply be:
```
parallel avidemux2 --load {} --save {.}.mkv --quit ::: *.proj
```
(I didn't include the donelist.txt tracking, because quite honestly it's stupid and useless — the existence of *output files* gives you the list of which jobs are done! And if whoever wrote that original script *really* wanted it to be a "done" list, they'd append to it **after** the jobs finish, not before they're started. As they coded it, it's utterly pointless.)

The parallel command above will run one conversion job per CPU core in parallel (that's its default), and keep each slot busy by starting the next one each time a job ends.

If you wanted to adjust the number of parallel jobs — say, if each job needs two cores to run — you could use parallel's -j argument at the start of the command line to make adjustments. You can allocate an explicit number of slots, or have it automatically compute the slots as a percentage of the core count, or add/subtract a certain number of slots from the core count.

All the rest of the syntactic magic, like {}, {.}, and :::, is explained in the man page. (Most of it's probably pretty intuitable, anyway. {.} is parallel's syntax for the input filename with the extension stripped off — roughly equivalent to zsh's ${VARIABLE:r} — which alleviates the need for that messy input-list preprocessing via cut.)

---

