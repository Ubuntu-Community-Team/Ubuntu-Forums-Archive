---
title: "LIRC Version Missmatch ?"
date: 2013-03-16
forum: Mythbuntu
---

### Post by gga96 on 2013-03-16
Hi All,

I am new to linux, but have installed MythBuntu and now have the front and back ends working well.
My task now is getting started with the remote control and lirc.

I understand the mythbuntu 12.04 release included the lirc pakage with this ditribution.

Google searches have provided conflicting advise on where different lirc files should be stored.

When I run "irrecord myremote" this is what I get...
"irrecord: could not get file information for /dev/lirc".

/dev is void of lirc files and it seems to me (on my system) most of the lirc files are located in /etc/lirc.

I am confused and would like help to get lirc sorted and setup correctly.

Any help will be apprciated.
Glen

---

### Post by Bullwinkle_Moose on 2013-03-16
Try creating a file with the name lircrc in /home/*username*/.mythtv (you can do **touch ~/.mythtv/lircrc** from a command prompt) and then open the lircrc file in a text editor and put into it something like this:

```
begin
 prog = mythtv
 button = KEY_1
 config = 1
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_2
 config = 2
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_3
 config = 3
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_4
 config = 4
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_5
 config = 5
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_6
 config = 6
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_7
 config = 7
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_8
 config = 8
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_9
 config = 9
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_0
 config = 0
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_BACK
 config = Esc
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_HOME
 config = O
 repeat = 0
end

begin
 prog = mythtv
 button = Guide
 config = M
 repeat = 0
end

begin
 prog = mythtv
 button = More
 config = I
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_VOLUMEDOWN
 repeat = 1
 config = F10
end

begin
 prog = mythtv
 button = KEY_VOLUMEUP
 repeat = 1
 config = F11
end

begin
 prog = mythtv
 button = KEY_CHANNELUP
 repeat = 3
 config = Up
end

begin
 prog = mythtv
 button = KEY_CHANNELDOWN
 repeat = 3
 config = Down
end

begin
 prog = mythtv
 button = KEY_UP
 repeat = 3
 config = Up
end

begin
 prog = mythtv
 button = KEY_DOWN
 repeat = 3
 config = Down
end

begin
 prog = mythtv
 button = KEY_LEFT
 repeat = 3
 config = Left
end

begin
 prog = mythtv
 button = KEY_RIGHT
 repeat = 3
 config = Right
end

begin
 prog = mythtv
 button = KEY_PLAY
 config = Return
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_OK
 config = Return
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_ENTER
 config = Return
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_MUTE
 config = |
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_REWIND
 config = <
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_FORWARD
 config = >
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_AGAIN
 config = Home
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_NEXT
 config = End
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_RECORD
 config = R
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_STOP
 config = Esc
 repeat = 0
end

begin
 prog = mythtv
 button = KEY_PAUSE
 config = P
 repeat = 0
end

# Use for backwards commercial skip
begin
 prog = mythtv
 button = Replay
 config = Q
 repeat = 0
end

# Use for forward commercial skip
begin
 prog = mythtv
 button = Skip
 config = Z
 repeat = 0
end

begin
 prog = mythtv
 button = LiveTV
 repeat = 3
 config = ALT+L
end

# Toggle subtitles (closed captions)
begin
 prog = mythtv
 button = Teletext
 config = T
 repeat = 0
end

begin
 prog = mythtv
 button = star
 config = W
 repeat = 0
end
```

The above is for a MCE compatible remote, so if you have a different kind of remote you may need to modify this.  You can run the command **irw** from a command prompt and then push buttons on the remote and it will show you the names of the button values that should be used in the lircrc file.  You then map those buttons to the keys that you would press on a keyboard to perform the desired function, using the config values.  The repeat values let you specify how many times you want to repeat the key with a single remote press.  So for example, pressing the Volume Up button on an MCE compatible remote generates KEY_VOLUMEUP (as viewed in irw), which is translated to the F11 keystroke and repeated once (so it's like pressing F11 twice).  Once you understand how it works, if you don't like the way a button is mapped you can change it to be whatever you want.

---

### Post by AlecJ on 2013-03-16
The best way is to use Myth Control Centre
It has all the common remotes listed.

---

### Post by gga96 on 2013-03-17
Thank you Bullwinkle_Moose for your help.

I have followed your advise but when I get to the point of running **irw** the following responses  occurs:
[B]glen@glen-myth:~$ irw -h
Usage: irw [socket]
     -h --help         display usage summary
     -v --version         display version
glen@glen-myth:~$ irw -v
irw 0.9.0
glen@glen-myth:~$ irw
connect: No such file or directory
glen@glen-myth:~$ sudo irw
[sudo] password for glen: 
connect: No such file or directory

[/B]I have uninstalled and then reinstalled** lirc **but still the same result.
Any thoughts on what has gone wong and the fix?

Glen

---

