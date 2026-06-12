---
title: "using a remote with SDLmame"
date: 2010-11-06
forum: Mythbuntu
---

### Post by rlongfield on 2010-11-06
I'm trying to get my remote to exit out of SDLmame so that I do not need to have a keyboard sitting around in my living room connected to my Mythtv box.

I am running Mythbuntu 10.04 with SDLmame 0.136 installed and working just fine.

I found this entry which says it should be put in ~/.lircrc but as I understand with mythbuntu it should be put in a file in ~/.lirc
I wasn't sure what to call the file so I create one called sdlmame and a second called irexec. 

Neither of these files causes the Back/Exit button press on my remote to function as the ESC key on the keyboard. 

Here is the content of the files (they are both exactly the same):

#this kills mame - not pretty, but it does the job as SDLMame does not support lirc
begin
    remote = hauppauge_pvr
    prog = irexec
    button = ESC
    config = killall mame
end

I've also tried this config for the files: 
#this kills mame - not pretty, but it does the job as SDLMame does not support lirc
begin
    remote = hauppauge_pvr
    prog = irexec
    button = Back/Exit
    config = Escape
end

It doesn't seem to make a difference. I would appreciate any help

---

