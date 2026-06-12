---
title: "REACT under WINE"
date: 2008-12-14
forum: Multimedia Software
---

### Post by lingenfr on 2008-12-14
I installed REACT2 (Exact Audio Copy (EAC) scripting GUI) under wine with Hardy. It runs OK, but I can't seem to create MP3's. I have enabled albumdownloader, but that does not launch when the encoding completes. My goal is to create 192kbs VBR MP3's. I want embedded albumart and I would like wavgain/mp3gain/or similar to encode all my MP3's at a consistent relative volume. My React.ini is posted below. If you see anything wrong or can point me in the right direction, thanks.

[Settings]
Version=2.0
ImageExt=wav
ImageNaming=$artist$ - $album$
ImageHotKey={F10}
TracksHotKey={F4}
TracksHotVal=+{F5}
VA=Various Artists
CreateAllCuesheets=0
RunCoverDownloader=1
CoverDownloader=C:\Program Files\REACT2\coverdownloader\albumart.exe
EAC=C:\Program Files\Exact Audio Copy\EAC.exe
Tools=C:\Program Files\REACT2\tools
MinimizeCompressionWindow=1
ProcessPriority=1
Sla_Bks_Col_Qst_Bar_Quo_Ast_Lt_Gt=-|-|-||!|'|#|[|]

[UserTrackFormats]
Flac=0
Wavpack=1
LameMP3=1
NeroAac=0
iTunesAac=0
OggEnc2=0

[UserOutputNames]
OutRoot=@mymusic@\
ImageDir_Flac=@OutRoot@\FLAC-images\$cdartist$
ImageDir_Wavpack=@OutRoot@\WV-images\$cdartist$
ImageDir_MP3=@OutRoot@\MP3-images\$cdartist$
TrackDir_Flac=@OutRoot@\FLAC\$cdartist$\[$year$] $album$
TrackDir_Wavpack=@OutRoot@\WV\$cdartist$\[$year$] $album$
TrackDir_MP3=@OutRoot@\$cdartist$
TrackDir_AAC=@OutRoot@\AAC\$cdartist$\[$year$] $album$
TrackDir_OGG=@OutRoot@\OGG\$cdartist$\[$year$] $album$
TrackName_SA=$album$ - $track$ - $title$
TrackName_VA=$album$ - $track$ - $title$ [$artist$]
TrackName_SA_acdir=$n - $~t
TrackName_VA_acdir=$n - $~t [$~a]

[UserSettings]
Debug=0
Comment=Created with EAC/REACT2, @curdate@
EmbedCover=1
ReplayGain=1
ApplyAlbumGain=1
AdjustAlbumGain_dB=+3.0
AddCuesheetAG=0
UseWaveGainAG=0
Opt_Flac=-5 -f
Opt_Wavpack=-hmy
Opt_LameMP3=-V2 --vbr-new --noreplaygain --nohist
Opt_NeroAac=-lc -q 0.21
Opt_iTunesAac=-d -s 2000
Opt_OggEnc2=-q 3.0
Ver_Flac=1.1.3
Ver_Wavpack=4.40
Ver_LameMP3=3.97
Ver_NeroAac=1.0.0.2
Ver_OggEnc2=2.83 Lancer aoTuV b5

---

### Post by ivanhelguera on 2009-07-10
Coverdownloader is .NET application, if memory serves, so it won't run unless you have MS's .NET installed under WINE, if I understand correctly.

---

