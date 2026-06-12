---
title: "Pipelight causes Rhythmbox to freeze"
date: 2014-06-04
forum: Multimedia Software
---

### Post by tholynch on 2014-06-04
Hello all,

I just installed the latest updates, which seems to have broken Rhythmbox. Before the update it worked just fine; however, it now freezes whenever I try to launch it. The only new packages to have been installed are:
```
libxcb-keysyms1:amd64
libxkbcommon-x11-0:amd64

```

I don't think the problem comes from either of these packages though, and here's why. Running Rhythmbox from Terminal gives the following output:
```

$ rhythmbox

(rhythmbox:3565): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed

(rhythmbox:3565): GLib-GObject-CRITICAL **: object SoupServer 0x7fc024002e50 finalized while still in-construction

(rhythmbox:3565): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/remember-the-rhythm/remember-the-rhythm.py", line 114, in init_source
    self.shell_player.jump_to_current()
gi._glib.GError: Could not locate rb_shell_player_jump_to_current: 'rb_shell_player_jump_to_current': /usr/lib/librhythmbox-core.so.8: undefined symbol: rb_shell_player_jump_to_current
[PIPELIGHT:LIN:unknown] attached to process.
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_SILVERLIGHT5_1_CONFIG.
[PIPELIGHT:LIN:unknown] searching for config file pipelight-silverlight5.1.
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/tlynch/.config/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/etc/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/usr/share/pipelight/configs/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:unknown] sandbox not found or not installed!
[PIPELIGHT:LIN:silverlight5.1] using wine prefix directory /home/tlynch/.wine-pipelight.
[PIPELIGHT:LIN:silverlight5.1] checking plugin installation - this might take some time.
[install-dependency] wine-silverlight5.1-installer is already installed in '/home/tlynch/.wine-pipelight'.
[install-dependency] wine-mpg2splt-installer is already installed in '/home/tlynch/.wine-pipelight'.
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
[PIPELIGHT:WIN:silverlight5.1] embedded mode         is on.
[PIPELIGHT:WIN:silverlight5.1] windowless mode       is off.
[PIPELIGHT:WIN:silverlight5.1] linux windowless mode is off.
[PIPELIGHT:WIN:silverlight5.1] force SetWindow       is off.
[PIPELIGHT:WIN:silverlight5.1] window class hook     is on.
[PIPELIGHT:WIN:silverlight5.1] strict draw ordering  is off.
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExA.
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExW.
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenuEx.
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenu.
fixme:advapi:RegisterTraceGuidsW (0x7022a7, 0x7a0120, {aa087e0e-0b35-4e28-8f3a-440c3f51eef1}, 1, 0x68f678, (null), (null), 0x7a0120): stub
[PIPELIGHT:WIN:silverlight5.1] init successful!
[PIPELIGHT:WIN:silverlight5.1] OpenGL Vendor: Intel Open Source Technology Center
[PIPELIGHT:WIN:silverlight5.1] OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile x86/MMX/SSE2
[PIPELIGHT:WIN:silverlight5.1] Your GPU is in the whitelist, hardware acceleration should work.
[PIPELIGHT:LIN:silverlight5.1] using thread asynccall event handling.
^C

```

Now, this seems to have something to do with Wine and the Pipelight plugin, which I have installed to watch Netflix on my laptop. I really don't see why it would be running with Rhythmbox, but my best guess is that it has something to do with Pulseaudio, seeing as it's the only thing Netflix and Rhythmbox have in common (at least, as far as I know).
I don't tend to pay much attention to the updates, but I vaguely recall seeing 'compholio' written somewhere in there, and since the problem seems to be related to his plugin, it seems reasonable to infer that this update may have caused my problems.

If any additional information is needed, please tell me so and I will post it as soon as possible.
Any help would be greatly appreciated.

---

### Post by monkeybrain20122 on 2014-06-04
Better ask the developers.
[https://answers.launchpad.net/pipelight](https://answers.launchpad.net/pipelight)

---

### Post by tholynch on 2014-06-04
Alright, I'll try that then.

---

