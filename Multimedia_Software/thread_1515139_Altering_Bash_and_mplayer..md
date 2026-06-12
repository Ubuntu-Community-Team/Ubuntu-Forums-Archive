---
title: "Altering Bash and mplayer."
date: 2010-06-21
forum: Multimedia Software
---

### Post by Axolotl9250 on 2010-06-21
Hi All, I downloaded mplayer and edited my bash the following way as seen on another thread:

```
# Check for an interactive session
[ -z "$PS1" ] && return

alias ls='ls --color=auto'
PS1='[\u@\h \W]\$ '

#########################
#Various Edits:
#########################
#This changes what the terminal displays before the cursor
export PS1="GLaDOS, "

alias sing='mplayer -really-quiet ~/Music/"stillalive.mp3" < /dev/null & echo -n "T" && sleep .05 && echo -n "h" && sleep .08 &&  echo -n "i" && sleep .05 && echo -n "s" && sleep .05 && echo -n " " && sleep .05 && echo -n "w" && sleep .1 && echo -n "a" && sleep .1 && echo -n "s" && sleep .03 && echo -n " " && sleep .05 && echo -n "a" && sleep .1 && echo -n " " && sleep .1 && echo -n "t" && sleep .1 && echo -n "r" && sleep .1 && echo -n "i" && sleep .1 && echo -n "u" && sleep .1 && echo -n "m" && echo -n "p" && sleep .1 && echo "h" && sleep 4.3 && echo "

                  .,-;;//;\=,. 
               . 1H@@@MM@M#H/ ,+;,
            ,/X+ +M@@M@MM% ,-%HMMM@X/,  
          -+@MM; SM@@MH+- ;XMMMM@MMMM@+-
         ,@M@@M- XM@X;. -+XXXXXHHH@M@M.--.    
        ,%MM@@MH ,@%=            ..--=-=;=,.
        +@#@@@MX .,              -%HXSS%%%+; 
       =; .@M@M$                  .;@MMMM@MM;
       X@= -#MM/                    .+MM@@@M#;
      ,@M@H; ;@1                     . =X#@@@@
      ,@@@MMX, .                    /H- ;@M@M=
      .H@@@@M@+,                    %MM+. %#$.
       /MMMM@MMH\.                  XM@MH; =;
        /%+%SXHH@#=              , .H@@@@MX,
         .,,.,,..,,,           -%H ,@@@@@MX,  
          %MM@@@HHHXM++;;-- .;SMMX =M@@MM%. 
           =XMCAMAMAGUEY ,-+HMM@M+ /MMMX=
             =%@M@M#@S .=#@MM@@@M; %M%=
               ,;+#+- /H#MMMMMMM@= =,
                 --. =++%%%%+/;-.
"'
```But when I try to load my mp3 I get the following two errors:
```
mplayer: could not connect to socket
mplayer: No such file or directory

```I'm not really sure what's going on here, I was just tinkering and learning about bash, wasn't expecting mplayer to go wrong. I won't carry on the lyrics after this first line after the error is displayed. Does anybody know whats up with it here?

[EDIT] I managed to get the errors to go away by putting 
nolirc=yes
in my mplayer.conf file.

Now it will print the line "This was a Triumph" and then display The aperture logo and then not print
anymore lyrics, I don't know if this is all it should do or if it should print all lyrics, I think it should 
print all.

---

