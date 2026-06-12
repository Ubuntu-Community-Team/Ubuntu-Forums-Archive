---
title: "Terminal problem in macOS 12 (Monterey)"
date: 2022-03-02
forum: Mac OSX
---

### Post by Penfold1971 on 2022-03-02
I'm in the process of migrating all of my work from an iMac running macOS 10.14.6 (Mojave) to a new iMac running macOS 12.2.1 (Monterey).

On the older system, I'd had an alias that I'd created in Terminal that enabled me to ssh into a machine running Ubuntu. It was (I'm not adept at Terminal commands - I was shown them by good folks on this site):
nano ~/.bash_profile (return)

alias fah='ssh [EMAIL="me@me-xxxxx-xxx-xx.local"]me@me-xxxxx-xxx-xx.local[/EMAIL]'

Then ControlO to save the alias and ControlX to exit nano.
Quit and re-open Terminal.

After that, all I had to do was type 'fah' (followed by the password for the Ubuntu machine).

The problem now is that the default shell displayed in Terminal on the new machine is 'zsh' and that command doesn't work.

Can anyone help me to create a new command for zsh?

I want to be able to do this because I'm running the Ubuntu machine without monitor, keyboard and mouse.

---

### Post by TheFu on 2022-03-02
I wouldn't expect zsh to use the bash_aliases file.  Which file is used normally for zsh aliases? Modify that.
But [https://zsh.sourceforge.io/Intro/intro_8.html](https://zsh.sourceforge.io/Intro/intro_8.html) has examples of zsh aliases.  Seems those should be the same. As a guess, I'd expect ~/.zshrc to the typical zsh startup file. Try that.

You could just change the default shell to bash.  **chsh** is the command for that. I don't know if there are addition impacts. zsh is sorta niche on Unix.  Probably a fine shell, but if you don't want to change, then you don't have to.

---

### Post by Penfold1971 on 2022-03-02
Thanks for your reply.

I tried substituting zsh for bash in the first command to make it:  [COLOR=#000000][FONT=&quot]nano ~/.zsh_profile[/FONT][/COLOR]
but it didn't work.

I'm a real amateur with this stuff. Just want to make it work.

I looked in the link you posted, but it was way above my head I'm afraid.

---

### Post by TheFu on 2022-03-02
You've completely lost me.

Did you put that same alias line in the ~/.zshrc file, logout, login, be happy?  Obviously, make the owner, group and permissions of the ~/.zshrc match whatever the old file used.

---

### Post by Penfold1971 on 2022-03-02
[COLOR=#1A1A1A][FONT=Verdana]Sorry if I haven't described what I did properly. I think you might need to shift down a few gears here. I'm really slow. [IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/24b76b19-4a6a-4adc-bb95-64e9e45f3fee[/IMG][/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]Originally in Terminal on my older iMac:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]nano ~/.bash_profile[FONT=Arial] *(return)*[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#D23212][FONT=&quot][COLOR=#1a1a1a]alias fah='ssh [EMAIL="me@me-xxxxx-xxx-xx.local"][COLOR=#d23212]me@me-xxxxx-xxx-xx.local[/COLOR][/EMAIL]'[/COLOR][/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]Followed by:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ControlO to save the alias and ControlX to exit nano.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]I attempted, on the  newer iMac:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]nano ~/.zsh_profile[FONT=Arial] *(return*[/FONT][/FONT][/COLOR]
[COLOR=#D23212][FONT=&quot][COLOR=#1a1a1a]alias fah='ssh [EMAIL="me@me-xxxxx-xxx-xx.local"][COLOR=#d23212]me@me-xxxxx-xxx-xx.local[/COLOR][/EMAIL]'[/COLOR][/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]Didn't work. &#8216;Command not found&#8217;, which makes me think the alias wasn&#8217;t saved.[/FONT][/COLOR]

---

### Post by TheFu on 2022-03-02
You have to logout and login to have the init files seen.

---

### Post by Penfold1971 on 2022-03-02
To show how slight my grasp is of all of this, what do you mean 'init files'?

Another question - when I use the Control+O followed by Controll+X, should the nano screen be replaced by the usual Terminal window I was in to begin with?

---

### Post by TheFu on 2022-03-02
init files === initialization files. I was just lazy.  

At login, on every Unix-like OS, including OSX, Linux, Unix, UNIX, AIX, HP-UX, Solaris, Digital Unix, and all the BSDs ... there is an order for which files get looked at and "sourced" to run programs.  We only care about init files for end-user logins.  Those are shell specific and usually clearly documented.  But, since these init files are little scripts, they can (and do) include other files to add more settings and start other programs.  I don't use zsh, but every other shell does this.  The default file - the init file - for zsh is ~/.zshrc.  It is hard coded in the program.  ~/.zshrc is identical to $HOME/.zshrc.

I don't use nano and purge it from all my systems as a matter of policy to prevent ever seeing it. Sorry.  There's usually a menu at the bottom showing the commands, if I recall correctly.  Why use nano if that is hard?  Use whatever editor you like. There must be 50 of them.

---

