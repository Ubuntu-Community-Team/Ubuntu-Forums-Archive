---
title: "Rhythmbox: LIRC plugin does not work"
date: 2009-02-11
forum: Multimedia Software
---

### Post by unimatrix on 2009-02-11
Hello. I got my remote working, but Rhythmbox doesn't seem to understand the signals it's getting.

When I run rhythmbox like this:
```
rhythmbox -d 2>&1 | grep lirc
```
And press some buttons on my remote (for example Play, Stop, Previous, Next) this is what I get:

> 
(14:29:09) [0x1b3c500] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/rblirc/lirc.rb-plugin
(14:29:09) [0x1b3c500] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/rblirc/lirc.rb-plugin
(14:29:09) [0x1b3c500] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/rblirc/librblirc.so
(14:29:09) [0x1b3c500] [register_rb_plugin] rb-lirc-plugin.c:91: Registering plugin RBLircPlugin
(14:29:09) [0x1b3c500] [rb_lirc_plugin_init] rb-lirc-plugin.c:104: RBLircPlugin initialising
(14:29:09) [0x1b3c500] [impl_activate] rb-lirc-plugin.c:202: Activating lirc plugin
(14:29:09) [0x1b3c500] [rb_plugin_find_file] rb-plugin.c:263: found '/usr/lib/rhythmbox/plugins/rblirc/rhythmbox_lirc_default' when searching for file 'rhythmbox_lirc_default' for plugin 'rblirc'
(14:29:19) [0x1b3c500] [rb_lirc_plugin_read_code] rb-lirc-plugin.c:136: unknown LIRC code "0000000083227986 00 Play Creative_RM-1500
(14:29:20) [0x1b3c500] [rb_lirc_plugin_read_code] rb-lirc-plugin.c:136: unknown LIRC code "000000008322857a 00 Stop Creative_RM-1500
(14:29:27) [0x1b3c500] [rb_lirc_plugin_read_code] rb-lirc-plugin.c:136: unknown LIRC code "0000000083227f80 00 Previous Creative_RM-1500
(14:29:29) [0x1b3c500] [rb_lirc_plugin_read_code] rb-lirc-plugin.c:136: unknown LIRC code "0000000083227a85 00 Next Creative_RM-1500
(14:29:37) [0x1b3c500] [impl_deactivate] rb-lirc-plugin.c:236: Deactivating lirc plugin


This is the lirc config file I'm using:
[http://lirc.sourceforge.net/remotes/creative/RM-1500](http://lirc.sourceforge.net/remotes/creative/RM-1500)

---

### Post by unimatrix on 2009-02-12
bump?

---

### Post by unimatrix on 2009-02-13
OK solved it myself.

What I had to do was use a correct .lircrc file (note: the lircrc entries called button= must relate to button names in /etc/lirc/lircd.conf)

Here is my .lircrc file that works with Rhythmbox:
```

##
# Rhythmbox key bindings.
##
begin
        prog = Rhythmbox
        button = Play
        config = playpause
end
begin
        prog = Rhythmbox
        button = Pause
        config = playpause
end
begin
        prog = Rhythmbox
        button = Stop
        config = stop
end
begin
        prog = Rhythmbox
        button = Step
        config = seek_forward
end
begin
        prog = Rhythmbox
        button = Slow
        config = seek_backward
end
begin
        prog = Rhythmbox
        button = Next
        config = next
end
begin
        prog = Rhythmbox
        button = Previous
        config = previous
end

```

---

### Post by Ceyx on 2011-02-16
Thanks for the info !

I've done a little how-to at [http://tech.quagmire.ca](http://tech.quagmire.ca)

---

