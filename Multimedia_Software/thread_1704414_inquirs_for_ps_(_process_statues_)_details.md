---
title: "inquirs for ps ( process statues ) details"
date: 2011-03-10
forum: Multimedia Software
---

### Post by MODYSAMA on 2011-03-10
*[COLOR=#002060]Hello, Can I get help.[/COLOR]*
*[COLOR=#002060]I tried to collect everything related to ps command line.[/COLOR]*
[I][COLOR=#002060]I have OS: Kubnutu 10.10 
[/COLOR][/I]
*[COLOR=#002060]Using ps ux command, I want to get clear with it's all details.[/COLOR]*
[I][COLOR=#002060]Can anyone list me description for each of the following?
[/COLOR][/I]
*[COLOR=#002060]I'd be grateful.[/COLOR]*[B][I][U][COLOR=#002060]
[/COLOR][/U][/I][/B]
*_[COLOR=#002060]Title:[/COLOR]_*
   
          > PID
          
             %CPU
          
             %MEM
          
             VSZ
          
             RSS
          
             TTY
          
             STAT
          
             TIME
          
             COMMAND  
          
         
  _*[COLOR=#002060]TTY can be:[/COLOR]*_
  
          > ?
          
             pts/1
          
             pts/2
          
         
   
  *_[COLOR=#002060]Statues can be:[/COLOR]_*
  > 
          S
          
             S+
          
             Ss
          
             SN
          
             Sl
          
             Sl+
          
             SNl
          
             Ss+
          
             R
          
             R+
          
             S<sl

---

### Post by Zorael on 2011-03-10
This is what the **man** tool is for. If you run '**man ps**' in a terminal, it will display the **man**ual for ps. Specifically see the *Standard Format Specifiers* and *Process State Codes* sections. As for the tty field, that probably just lists which tty the process is running in.

Googling turns up with results like [this page](http://unixhelp.ed.ac.uk/CGI/man-cgi?ps) that mirrors the contents of said manual.

---

### Post by MODYSAMA on 2011-03-11
**[Zorael]("http://ubuntuforums.org/member.php?u=266856"),**
many thanks.

---

