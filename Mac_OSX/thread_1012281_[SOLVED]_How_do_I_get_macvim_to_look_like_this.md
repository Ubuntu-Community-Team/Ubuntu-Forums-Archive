---
title: "[SOLVED] How do I get macvim to look like this?"
date: 2008-12-15
forum: Mac OSX
---

### Post by Redrazor39 on 2008-12-15
The screenshot attached has a pic of MacVim and I want it to look like the black transluscent one. Could you please tell me how to do that?

Thanks.

---

### Post by Redrazor39 on 2008-12-16
Oh come on. Nobody is helping?

---

### Post by Redrazor39 on 2008-12-16
Ok no worries I got it. For anyone who wants to know, you have to open macvim, type

```
:edit .gvimrc
```

then at the end of that file add these lines:

```
set transparency=10
colorscheme pablo

```
Then save and quit by typing :wq

and then to hide the toolbar (which sucks IMHO) by default, open a new MacVim window and type

```
:edit .vimrc
```

Then at the end of that file, add these lines

```
if has("gui_running")
    set guioptions=egmrt
endif
```

Optionally, if you want the text to wrap properly (without breaking your words), add this to the same .vimrc file (at the end)
```

set wm=4
```


I'm pretty sure all of this will work with any GUI vim (GVim, MacVim, etc.) In versions of VIM that run completely in the terminal, you only edit your .vimrc file for settings. 

I hope this helps any new VIM users-- I had to scour the net for hours just to find simple stuff like this.

---

