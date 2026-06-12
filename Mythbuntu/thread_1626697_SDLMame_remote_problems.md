---
title: "SDLMame remote problems"
date: 2010-11-20
forum: Mythbuntu
---

### Post by rlongfield on 2010-11-20
Ièm trying to get my remote working with SDLmame .16 on my 10.04 Myhbuntu box. 

I followed the directions in the mythgame wiki which said that placing these commands in ./lircrc. I created an include in .lircrc to a file in .lirc called sdlmame.

#this kills mame - not pretty, but it does the job as SDLMame does not support lirc
begin
remote = hauppauge_pvr
prog = irexec
button = ESC
config = killall mame
end

This does not exit sdlmame and irexec is running on startup. I am wondering if I need to run xmacro-wrap or not

---

