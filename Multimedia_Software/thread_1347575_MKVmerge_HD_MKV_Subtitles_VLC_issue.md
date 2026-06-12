---
title: "MKVmerge HD MKV Subtitles VLC issue"
date: 2009-12-06
forum: Multimedia Software
---

### Post by alejandro.mc on 2009-12-06
So this is the problem, I use MKVMergeGUI to add a .srt to a .MKV, I muxe it correctly, but when I play the .MKV with VLC, the "ñ", and the "é""á""ó""í""ú""?""!". I've selected the subtitle as UTF-8 (they told me it works fine with spanish charset) in VLC but the issue is still there.

Any ideas?

Thanks in advance,

Alejandro.

---

### Post by lovinglinux on 2009-12-06
I think the way to fix this is to open VLC preferences and change the Default Encoding settings in the Subtitles & OSD section, according to your language. Nevertheless, I couldn't find the correct option for my language there. So I guess this is why the automatic selection of encoding is not working and the subtitles are messed up.

If this is your case, I would recommend converting the subtitle file to ssa before muxing it. I use Jubler to do this. You can get it at getdeb.net. Simply open the subtitle file with jubler using the correct encoding options, than save it. The saving dialog will ask for the desired subtitle format, in this case ssa, and the encoding. Select the proper encoding for your language and save it. Then mux this ssa subtitle with mkvtoolnix and it will be displayed correctly on VLC.

I don't use VLC, since I prefer smplayer, but I have made a test and it works.

---

### Post by alejandro.mc on 2009-12-06
Thanks a lot I'll be trying it in a minute!

I'll let you know!

Bye!

---

### Post by alejandro.mc on 2009-12-06
Great it worked like a charm!

Thanks a lot!!!!!!!!!!!

Best of lucks!!

Alejandro.

PD: I love this community!

---

### Post by lovinglinux on 2009-12-07
> **alejandro.mc said:**
> Great it worked like a charm!

Thanks a lot!!!!!!!!!!!

Best of lucks!!

Alejandro.

PD: I love this community!

You are welcome. Did you change the encoding or converted the subtitle to ssa?

---

### Post by alejandro.mc on 2009-12-07
I used to try with UTF-8 but then I changed to ISO8859-1, then muxed with MKVmerge and I selected in VLC the ISO8859-1 encoding, and

VOILAAAA!!

Thanks a lot! Now I can backup my MKVs with subtitles at last, I had almost 200 GB of them.. =)

Bye,

Alejandro.

---

