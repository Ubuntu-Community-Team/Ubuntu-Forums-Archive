---
title: "Wired for Ubuntu"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-09-02
Hi all,

I've been quite annoyed lately by the continuous crashes of Rosegarden (and by the impossibility to switch off the metronome -- but maybe it was just my ignorance), so I went surfing around and found an excellent piece of software, [Wired]("http://wired.is.free.fr/"). The only problem is that on the website they only provide the source, and not a .deb package...

I'm not good at all at creating .deb packages (and I'm a bit worried about messing around with ./configure, make and make install, since so many times I've not been able to uninstall what I had installed)...

Does anybody know if there is any Ubuntu package available around?

Thanks for your time

---

### Post by skymt on 2006-09-02
Just install checkinstall (sudo apt-get install checkinstall). Then run ./configure, make, sudo checkinstall, and it'll make and install a .deb for you.

---

### Post by finferflu on 2006-09-02
> **skymt said:**
> Just install checkinstall (sudo apt-get install checkinstall). Then run ./configure, make, sudo checkinstall, and it'll make and install a .deb for you.

It sounds very good, does it mean that I can uninstall it with **sudo apt-get remove**?


--EDIT--

Yes it does, sort of:

 ```
Done. The new package has been installed and saved to

 /home/mmanu/wired-0.2.2/portaudio/portaudio_2.0-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r portaudio
```

Thanks a lot for the useful hint!

---

### Post by finferflu on 2006-09-02
Too bad, I couldn't *make it* until the sudo checkinstall:

```
ChannelGui.cpp:88: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:103: error: variable or field ‘OnFaderLeft’ declared void
ChannelGui.cpp:103: error: ‘int ChannelGui::OnFaderLeft’ is not a static member of ‘class ChannelGui’
ChannelGui.cpp:103: error: ‘wxScrollEvent’ was not declared in this scope
ChannelGui.cpp:103: error: ‘e’ was not declared in this scope
ChannelGui.cpp:103: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:104: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:125: error: variable or field ‘OnFaderRight’ declared void
ChannelGui.cpp:125: error: ‘int ChannelGui::OnFaderRight’ is not a static member of ‘class ChannelGui’
ChannelGui.cpp:125: error: ‘wxScrollEvent’ was not declared in this scope
ChannelGui.cpp:125: error: ‘e’ was not declared in this scope
ChannelGui.cpp:125: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:126: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:152: error: expected ‘,’ or ‘...’ before ‘&’ token
ChannelGui.cpp:152: error: ISO C++ forbids declaration of ‘wxString’ with no type
ChannelGui.cpp: In member function ‘void ChannelGui::SetLabel(int)’:
ChannelGui.cpp:154: error: ‘label’ was not declared in this scope
ChannelGui.cpp:158: error: expected `;' before ‘s’
ChannelGui.cpp:159: error: ‘s’ was not declared in this scope
ChannelGui.cpp:161: error: ‘Label’ was not declared in this scope
ChannelGui.cpp:164: error: ‘Label’ was not declared in this scope
ChannelGui.cpp: In member function ‘void ChannelGui::UpdateScreen()’:
ChannelGui.cpp:177: error: ‘MixMutex’ was not declared in this scope
ChannelGui.cpp: At global scope:
ChannelGui.cpp:189: error: variable or field ‘OnMuteLeft’ declared void
ChannelGui.cpp:189: error: ‘int ChannelGui::OnMuteLeft’ is not a static member of ‘class ChannelGui’
ChannelGui.cpp:189: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:189: error: ‘e’ was not declared in this scope
ChannelGui.cpp:189: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:190: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:212: error: variable or field ‘OnMuteRight’ declared void
ChannelGui.cpp:212: error: ‘int ChannelGui::OnMuteRight’ is not a static member of ‘class ChannelGui’
ChannelGui.cpp:212: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:212: error: ‘e’ was not declared in this scope
ChannelGui.cpp:212: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:213: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:235: error: variable or field ‘OnLock’ declared void
ChannelGui.cpp:235: error: ‘int ChannelGui::OnLock’ is not a static member of ‘class ChannelGui’
ChannelGui.cpp:235: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:235: error: ‘e’ was not declared in this scope
ChannelGui.cpp:235: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:236: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:244: error: ‘wxImage’ has not been declared
ChannelGui.cpp:245: error: ‘wxImage’ has not been declared
ChannelGui.cpp:245: error: ‘wxWindow’ has not been declared
ChannelGui.cpp:246: error: ‘wxWindowID’ has not been declared
ChannelGui.cpp:246: error: expected ‘,’ or ‘...’ before ‘&’ token
ChannelGui.cpp:247: error: ISO C++ forbids declaration of ‘wxPoint’ with no type
ChannelGui.cpp: In constructor ‘MasterChannelGui::MasterChannelGui(Channel*, int*, int*, int*, int, int)’:
ChannelGui.cpp:248: error: ‘pos’ was not declared in this scope
ChannelGui.cpp:248: error: ‘size’ was not declared in this scope
ChannelGui.cpp:248: error: ‘_’ was not declared in this scope
ChannelGui.cpp: At global scope:
ChannelGui.cpp:258: error: variable or field ‘OnFaderLeft’ declared void
ChannelGui.cpp:258: error: ‘int MasterChannelGui::OnFaderLeft’ is not a static member of ‘class MasterChannelGui’
ChannelGui.cpp:258: error: ‘wxScrollEvent’ was not declared in this scope
ChannelGui.cpp:258: error: ‘e’ was not declared in this scope
ChannelGui.cpp:259: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:283: error: variable or field ‘OnFaderRight’ declared void
ChannelGui.cpp:283: error: ‘int MasterChannelGui::OnFaderRight’ is not a static member of ‘class MasterChannelGui’
ChannelGui.cpp:283: error: ‘wxScrollEvent’ was not declared in this scope
ChannelGui.cpp:283: error: ‘e’ was not declared in this scope
ChannelGui.cpp:284: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:306: error: variable or field ‘OnMuteLeft’ declared void
ChannelGui.cpp:306: error: ‘int MasterChannelGui::OnMuteLeft’ is not a static member of ‘class MasterChannelGui’
ChannelGui.cpp:306: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:306: error: ‘e’ was not declared in this scope
ChannelGui.cpp:306: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:307: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:329: error: variable or field ‘OnMuteRight’ declared void
ChannelGui.cpp:329: error: ‘int MasterChannelGui::OnMuteRight’ is not a static member of ‘class MasterChannelGui’
ChannelGui.cpp:329: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:329: error: ‘e’ was not declared in this scope
ChannelGui.cpp:329: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:330: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:352: error: variable or field ‘OnLock’ declared void
ChannelGui.cpp:352: error: ‘int MasterChannelGui::OnLock’ is not a static member of ‘class MasterChannelGui’
ChannelGui.cpp:352: error: ‘wxCommandEvent’ was not declared in this scope
ChannelGui.cpp:352: error: ‘e’ was not declared in this scope
ChannelGui.cpp:352: error: ‘WXUNUSED’ was not declared in this scope
ChannelGui.cpp:353: error: expected ‘,’ or ‘;’ before ‘{’ token
ChannelGui.cpp:361: error: ‘wxPanel’ has not been declared
ChannelGui.cpp:362: error: expected constructor, destructor, or type conversion before ‘EVT_COMMAND_SCROLL’
make[2]: *** [ChannelGui.o] Error 1
make[2]: Leaving directory `/home/mmanu/wired-0.2.2/src/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mmanu/wired-0.2.2/src'
make: *** [all-recursive] Error 1
```

And this is only the last part of the output, I couldn't get hold of the rest..

---

### Post by skymt on 2006-09-02
Looks like you don't have all the requirements. Try installing libwxbase2.6-dev and libwxgtk2.6-dev. Also, it looks from the Wired website like there's a separate libraries download (wired-libs-0.2.tar.gz). You should probably install that first.

---

### Post by finferflu on 2006-09-03
Thanks!! It worked... I think I was rushing too much and not paying proper attention to what I was doing...

Now it's time to figure out how to configure everything on Wired, since there is no documentation whatsoever. Good luck to me!

---

