---
title: "Shell scripting"
date: 2010-05-18
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-18
I've realised that I will be more able to achieve some of the things I want in Mythbuntu if I have a good knowledge of shell scripting, such that I can write my own scripts or safely modify those written by others.

Can anyone recommend a good (and preferably free) tutorial?

---

### Post by ian dobson on 2010-05-18
Hi,

With scripting do you mean Bash or perl or awk. With bash you just use standard commands (ls,df,ps) feeding the output into variables.

Perl is more a programming language that allows you to add extra modules for extra functions (tcp sockets, mysql database access), if you already know a programming language then perl shouldn't be too hard to learn.

awk is a text processing language that can very quickly search/sort/cut strings.

Here's an example of a simple bash script:-

```

cat $FILE| while read LINE
do
   SENDER_IP=`echo $LINE| awk '{ print $3 }'| sed -e 's/\"//g'`                         #Get IP Address
echo $SENDER_IP
done

```

This script loops though each line of a file (in $FILE), calling echo to pass the line to awk which prints the third word in the line, then removing the " from the variable and saving the result to the variable SENDER_IP.

Just google for perl or bash or awk, you'll find lots of information. And yes linux was and still is an operating system for programmers, even if it's learnt alot in the last few years.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-18
I think I meant Bash scripts. I'm thinking of the scripts that end in .sh. That's Bash, right?

(As you see, I'm a bit of a newbie!)

---

### Post by ian dobson on 2010-05-18
Hi,

"Bash" scripts usually start with a #!/bin/sh the #! on the first line tells linux to use /bin/sh to process the file.

**BUT** /bin/sh is a symbolic link to bash or dash or some other shell. The difference between bash and dash are small and for a beginner you won't even know/see the difference apart from the fact dash is abit quicker/uses less memory.

Regards
Ian Dobson

---

### Post by jmlott on 2010-05-19
As far as free Bash Scripting information goes, this is arguably the best reference you will ever see.

[Advanced Bash-Scripting Guide]("http://http://tldp.org/LDP/abs/html/")

Bash, in general, is great for automating simple tasks. It can start getting unwieldy for more complicated things, though. If you find yourself needing more powerful logic, while maintaining a simple syntax, I would suggest looking into Python. It can do everything from simple one-liners to large object-oriented projects. There are tons of great books on it including [this one]("http://diveintopython.org/") which can be read entirely online (or downloaded) for free.

---

### Post by laffinet on 2010-05-19
I found the best way to get into scripting is to 

1. Analyse existing scripts (could be from these forums, other internet sites) that do something you're trying to achieve, try to understand every single bit of them
2. Modify scripts to suit your needs
3. Start writing your own scripts for task you'd like to automate

Lots of resources on the net:
[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html")
[http://www.linux.org/lessons/advanced/x1110.html]("http://www.linux.org/lessons/advanced/x1110.html")

Plus just google specific problems.

---

### Post by NautiusMaximus on 2010-05-20
Thanks! Those links look like just the sort of thing I'm looking for.

---

### Post by jb5 on 2010-05-23
> **jmlott said:**
> 
[Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/html/")


Above reference seemed to be borked. Changed to intended site?

---

### Post by kleskjr on 2010-05-23
> **jb5 said:**
> Above reference seemed to be borked. Changed to intended site?

seems he meant [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

