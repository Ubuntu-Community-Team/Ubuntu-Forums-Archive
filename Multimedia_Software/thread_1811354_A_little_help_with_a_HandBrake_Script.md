---
title: "A little help with a HandBrake Script"
date: 2011-07-24
forum: Multimedia Software
---

### Post by xlr8ed on 2011-07-24
Hello, Looking for a bit of help to combine a bunch of similar scripts.

A Little Background:
My wife is a travel nurse, and is sometimes gone for weeks at a time. When she is away I record her favorite shows on our Tivo, I then transfer then to my desktop to pull out the commercials and free up space on the Tivo. After that's done, I pull move them to a show directory on my Ubuntu Server and the script below take over because they are still really big files and my server is a lot more powerful then my desktop.

Right now I have a script like the one above for **each** one of her shows. The scripts run on a Cron, grab the shows, converts them, transfer them to a new directory for DLNA to serve, and then moves the original file to a Completed directory to be later deleted.

```
#!/bin/bash
#
# Change this to specify a different handbrake preset. You can list them by running: "HandBrakeCLI $
#
if [ -z "$1" ] ; then
TRANSCODEDIR="/storage00/Temp/TV/Cakes Show"
else
TRANSCODEDIR="$1"
fi
#finds all files recursively in folders and converts them to mp4
find "$TRANSCODEDIR"/* -type f -exec bash -c 'HandBrakeCLI -i "$1" -o "${1%\.*}".mp4 -E AAC -e x264 -f MP4' __ {} \;

#Change to the correct directory
cd "/storage00/Temp/TV/Cakes Show"
#move .mp4 to the directory below for DLNA
mv *.mp4 "/storage00/Video/Share/TV Shows/Cakes Show"
#move the original folder so it doesn't convert again
mv *.* /storage00/Temp/TV/Completed

```


The process works the way I want it to, but I really want it down to one script if it's possible. I would like it to just look in the /storage00/Temp/TV/ directory, convert the files, and then when it's done, move the file to the appropriate directory under /storage00/Temp/TV/[Show Name], while still moving the original file to a Completed directory.  

If it matters the actual video files are always named just like the directory but it also has the episode number. So for the script above, the file name would be "Cakes Show - E01"

---

### Post by JohnAStebbins on 2011-07-25
I'm working on a batch script that you might find useful.  It is not very well tested yet, and the gui mode is non-functional.  But the cli mode is complete.  It's written in python.

I think it's recursive processing option might be useful for your situation.  If all the "shows" are placed in subdirectories of one top level source directory, you can recursively encode all subdirs.  The script will create the corresponding subdirectories for the output under the destination directory you specify.

It doesn't move the source files when complete.  You would have to add that if it's required.  It will skip transcoding any file it finds already exists in the destination.  So if you are moving the files in order to avoid re-encoding the same file again, you might not need that.

pyhb.py --help
```
pyhb.py [-s <srcdir>] [-d <dstdir>] [-ehHn] [-- HandBrakeCLI-options]
    -s --srcdir       - Source directory of files to transcode. Default './'
    -d --dstdir       - Target directory of new transcoded files. Default './'
    -r --recursive    - Recursively process all subdirectories.
    -e --ext          - Set the source extensions to match.
                        Default ts,mp4,m4v,avi,mkv,mov,wmv,iso,vob
    -p --presets-file - Load custom preset file.
    -L --log-dir      - Directory where activity logs are stored.
    -I --instances    - Set number of simultaneous encodes.
    -h --help         - Show this message.
    -H --cli-help     - Show HandBrakeCLI help.
    -n --dryrun       - Show what would be done, but do nothing.

```

It can use custom presets that you have created with the handbrake gui.  It creates activity log files for all encodes in the same place as the gui does (~/.config/ghb/EncodeLogs).  It can lanuch multiple instances of HandBrakeCLI simultaneously in order to more fully utilize the CPU.  You can set a list of file name extensions to match when searching for files to transcode. You can add any additional HandBrakeCLI options you like (after a "--" on the command line).

example:
```

pyhb.py -s "/storage00/Temp/TV" -d "/storage00/Video/Share/TV Shows" -r -- -Z MyCustomPreset

```

script:
```


#!/usr/bin/env python

import os
import sys
import getopt
import re
import subprocess
import signal
import time
import string
import plistlib
import types
import time

gui = True
try:
    import pygtk
    pygtk.require('2.0')
    import gtk, gobject, glib
except ImportError:
    gui = False
gui=False

# If HandBrakeCLI is in your path...
#hbcli = "HandBrakeCLI"
# Otherwise, specify it's complete path
hbcli = "~/Source/hb/HandBrake/build.dbg/HandBrakeCLI"
def_ext = "ts,mp4,m4v,avi,mkv,mov,wmv,iso,vob"
dryrun = False

if sys.platform == "darwin":
    def_presets_plist = os.path.expanduser(
            "~/Library/Application Support/HandBrake/UserPresets.plist")
    def_log_dir = os.path.expanduser(
            "~/Library/Application Support/HandBrake/EncodeLogs")
elif sys.platform.startswith("linux"):
    def_presets_plist = os.path.expanduser("~/.config/ghb/presets")
    def_log_dir = os.path.expanduser("~/.config/ghb/EncodeLogs")
else:
    def_presets_plist = None
    def_log_dir = None

tmp = open("./bhb.ui", "r")
bhb_ui = tmp.read()

def usage(cmd):
    global gui

    print "%s [-s <srcdir>] [-d <dstdir>] [-ehHn] [-- HandBrakeCLI-options]" % os.path.basename(cmd)
    print "    -s --srcdir       - Source directory of files to transcode. Default './'"
    print "    -d --dstdir       - Target directory of new transcoded files. Default './'"
    print "    -r --recursive    - Recursively process all subdirectories."
    print "    -e --ext          - Set the source extensions to match."
    print "                        Default %s" % def_ext
    print "    -p --presets-file - Load custom preset file."
    print "    -L --log-dir      - Directory where activity logs are stored."
    print "    -I --instances    - Set number of simultaneous encodes."
    print "    -h --help         - Show this message."
    print "    -H --cli-help     - Show HandBrakeCLI help."
    print "    -n --dryrun       - Show what would be done, but do nothing."
    if gui:
        print "    -g --gui          - Launch GUI"


def print_command(cmd):
    if type(cmd).__name__ == 'str':
        print cmd
        return

    # else assume it's a list
    cmd_str = ""
    for arg in cmd:
        if string.find(arg, " ") != -1:
            # has spaces
            cmd_str += "\"" + arg + "\" "
        else:
            cmd_str += arg + " "

    print cmd_str

class UIManager:
    ui = None
    allow_cb = True
    callback = None

    def __init__(self, ui_str):
        # Don't step on preference values with defaults from UI xml
        self.allow_cb = False

        # Create the UI
        self.ui = gtk.Builder()
        self.ui.add_from_string(ui_str)
        self.connect()

        objects = self.ui.get_objects()
        for obj in objects:
            if not isinstance(obj, gtk.Buildable):
                continue
            value = self.widget_value(obj)
            name = gtk.Buildable.get_name(obj)
            self.__dict__[name] = value

        self.allow_cb = True

    def main_loop(self):
        gtk.main()

    def set_callback(self, callback):
        self.callback = callback

    def widget_value(self, widget):
        if widget.__gtype__ == gtk.SpinButton.__gtype__:
            return widget.get_value()
        elif widget.__gtype__ == gtk.CheckButton.__gtype__:
            return widget.get_active()
        elif widget.__gtype__ == gtk.FileChooserButton.__gtype__:
            return widget.get_filename()
        elif widget.__gtype__ == gtk.Label.__gtype__:
            return widget.get_text()
        elif widget.__gtype__ == gtk.Entry.__gtype__:
            return widget.get_text()
        elif widget.__gtype__ == gtk.ComboBox.__gtype__:
            return widget.get_active_text()
        elif widget.__gtype__ == gtk.Calendar.__gtype__:
            yy, mm, dd = widget.get_date()
            mm += 1
            return (yy, mm, dd)
        elif widget.__gtype__ == gtk.ProgressBar.__gtype__:
            return widget.get_fraction()
        else:
            return None

    def update(self, obj):
        value = self.widget_value(obj)
        name = gtk.Buildable.get_name(obj)
        if value != None:
            self.__dict__[name] = value
        return name, value

    def set_widget(self, name, value):
        # Check if the gtkbuilder object has been created
        if self.ui == None:
            return False
        # Check if we are setting a widget
        widget = self.ui.get_object(name)
        if widget == None:
            return False
        if widget.__gtype__ == gtk.SpinButton.__gtype__:
            widget.set_value(value)
        elif widget.__gtype__ == gtk.CheckButton.__gtype__:
            widget.set_active(value)
        elif widget.__gtype__ == gtk.FileChooserButton.__gtype__:
            widget.set_filename(value)
        elif widget.__gtype__ == gtk.Label.__gtype__:
            widget.set_text(value)
        elif widget.__gtype__ == gtk.Entry.__gtype__:
            widget.set_text(value)
        elif widget.__gtype__ == gtk.ComboBox.__gtype__:
            index = search_model_index(widget.get_model(), 0, value)
            if index != None:
                widget.set_active(index)
        elif widget.__gtype__ == gtk.Calendar.__gtype__:
            yy, mm, dd = value
            widget.select_month(mm-1, yy)
            widget.select_day(dd)
        elif widget.__gtype__ == gtk.ProgressBar.__gtype__:
            if type(value).__name__ == 'str':
                widget.set_text(value)
            elif type(value).__name__ == 'float':
                widget.set_fraction(value)
            elif type(value).__name__ == 'bool':
                widget.pulse()

        return True

    def __setattr__(self, name, value):
        self.__dict__[name] = value
        self.set_widget(name, value)

    # Connect UI signals
    def connect(self):
        signals = {
            "bhb_destroy_cb" : self.destroy_cb,
            "bhb_delete_cb"  : self.delete_cb,
            "bhb_action_cb"  : self.action_cb,
            "bhb_widget_changed_cb"  : self.widget_changed_cb
        }

        self.ui.connect_signals(signals, None)

    def delete_cb(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def destroy_cb(self, widget, data=None):
        gtk.main_quit()

    def action_cb(self, widget, data=None):
        name = gtk.Buildable.get_name(widget)
        print "Action %s" % name
        return

    def widget_changed_cb(self, widget, data=None):
        name, value = self.update(widget)
        if self.allow_cb and self.callback != None:
            self.callback(name, value)

class BHBGui:
    prefs = None
    uim = None

    def __init__(self, ui, batch, presets=None):
        self.uim = UIManager(ui)
        self.uim.set_callback(self.uim_cb)
        self.prefs = PrefManager()
        if self.prefs != None:
            for name, value in self.prefs.plist.items():
                setattr(self.uim, name, value)

    def uim_cb(self, name, value):
        if self.prefs != None and name in self.prefs.plist:
            self.prefs.update(name, value)

    def run(self):
        self.uim.main_loop()

class PrefManager:
    plist = None
    plistfile = None

    def __init__(self):
        global def_ext, def_presets_plist

        if sys.platform == "darwin":
            self.plistfile = os.path.expanduser(
                    "~/Library/Application Support/HandBrake/BHB.plist")
        elif sys.platform.startswith("linux"):
            self.plistfile = os.path.expanduser("~/.config/ghb/BHB.plist")
        else:
            return None

        if os.path.exists(self.plistfile):
            self.plist = plistlib.readPlist(self.plistfile)
        else:
            self.plist = { 
                "SourceDir" : ".",
                "DestDir" : ".",
                "Recursive" : False,
                "SourceExtensions" : def_ext,
                "PresetsFile" : def_presets_plist
            }
            plistlib.writePlist(self.plist, self.plistfile)

    def update(self, name, value):
        if value == None:
            return
        self.plist[name] = value
        plistlib.writePlist(self.plist, self.plistfile)

class HBPlist:
    plist = None
    dep_dict = {
        "VideoAvgBitrate" : tuple((
            tuple(("VideoQualityType",tuple((0, 1)))),
            )),
        "VideoQualitySlider" : tuple((
            tuple(("VideoQualityType", tuple((2,)))),
            )),
        "VideoTwoPass" : tuple((
            tuple(("VideoQualityType", tuple((0, 1)))),
             )),
        "VideoTurboTwoPass" : tuple((
            tuple(("VideoQualityType", tuple((0, 1)))),
            )),
        "VideoFramerateVFR" : tuple((
            tuple(("VideoFramerate", tuple(("Same as source",) ))),
            )),
        "Mp4LargeFile" : tuple((
            tuple(("FileFormat", tuple(("MP4 file",)))),
            )),
        "Mp4HttpOptimize" : tuple((
            tuple(("FileFormat", tuple(("MP4 file",)))),
            )),
        "Mp4iPodCompatible" : tuple((
            tuple(("FileFormat", tuple(("MP4 file",)))),
            tuple(("VideoEncoder", tuple(("H.264 (x264)",))))
            )),
        "PictureDeinterlace" : tuple((
            tuple(("PictureDecombDeinterlace", tuple((False,)))),
            )),
        "PictureDeinterlaceCustom" : tuple((
            tuple(("PictureDecombDeinterlace", tuple((False,)))),
            tuple(("PictureDeinterlace", tuple(("1",))))
            )),
        "PictureDecomb" : tuple((
            tuple(("PictureDecombDeinterlace", tuple((True,)))),
            )),
        "PictureDecombCustom" : tuple((
            tuple(("PictureDecombDeinterlace", tuple((True,)))),
            tuple(("PictureDecomb", tuple(("1",))))
            )),
        "PictureWidth" : tuple((
            tuple(("UsesPictureSettings", tuple((0, 1)))),
            )),
        "PictureHeight" : tuple((
            tuple(("UsesPictureSettings", tuple((0, 1)))),
            )),
        "PictureTopCrop" : tuple((
            tuple(("PictureAutoCrop", tuple((False,)))),
            )),
        "PictureBottomCrop" : tuple((
            tuple(("PictureAutoCrop", tuple((False,)))),
            )),
        "PictureLeftCrop" : tuple((
            tuple(("PictureAutoCrop", tuple((False,)))),
            )),
        "PictureRightCrop" : tuple((
            tuple(("PictureAutoCrop", tuple((False,)))),
            )),
        "PictureKeepRatio" : tuple((
            tuple(("PicturePAR", tuple((0, 3)))),
            )),
        "lavcOption" : tuple((
            tuple(("VideoEncoder", tuple(("MPEG-2 (FFmpeg)", "MPEG-4 (FFmpeg)")))),
            )),
        "x264Option" : tuple((
            tuple(("VideoEncoder", tuple(("H.264 (x264)",)))),
            )),
        "AudioBitrate" : tuple((
            tuple(("AudioEncoder", tuple(("AAC (faac)", "AAC (CoreAudio)", "AAC (ffmpeg)", "MP3 (lame)", "Vorbis (vorbis)", "AC3 (ffmpeg)")))),
            )),
        "AudioSamplerate" : tuple((
            tuple(("AudioEncoder", tuple(("AAC (faac)", "AAC (CoreAudio)", "AAC (ffmpeg)", "MP3 (lame)", "Vorbis (vorbis)", "AC3 (ffmpeg)")))),
            )),
        "AudioMixdown" : tuple((
            tuple(("AudioEncoder", tuple(("AAC (faac)", "AAC (CoreAudio)", "AAC (ffmpeg)", "MP3 (lame)", "Vorbis (vorbis)", "AC3 (ffmpeg)")))),
            )),
        "AudioTrackDRCSlider" : tuple((
            tuple(("AudioEncoder", tuple(("AAC (faac)", "AAC (CoreAudio)", "AAC (ffmpeg)", "MP3 (lame)", "Vorbis (vorbis)", "AC3 (ffmpeg)")))),
            )),
        "AudioTrackGain" : tuple((
            tuple(("AudioEncoder", tuple(("AAC (faac)", "AAC (CoreAudio)", "AAC (ffmpeg)", "MP3 (lame)", "Vorbis (vorbis)", "AC3 (ffmpeg)")))),
            )),
    }
    ndep_dict = {
        "VideoFrameratePFR" : tuple((
            tuple(("VideoFramerate", tuple(("Same as source",)))),
            )),
        "PictureWidth" : tuple((
            tuple(("PictureWidth", tuple((0,)))),
            )),
        "PictureHeight" : tuple((
            tuple(("PictureHeight", tuple((0,)))),
            )),
        "VideoFramerateVFR" : tuple((
            tuple(("VideoFramerateMode", tuple(("vfr", "pfr", "cfr")))),
            )),
    }

    xval = {
        # Output formats
        "MP4 file" : "mp4",
        "M4V file" : "m4v",
        "MKV file" : "mkv",
        # Video encoders
        "H.264 (x264)" : "x264",
        "MPEG-2 (FFmpeg)" : "ffmpeg2",
        "MPEG-4 (FFmpeg)" : "ffmpeg4",
        "MPEG-4 (XviD)" : "ffmpeg4",
        "VP3 (Theora)" : "theora",
        # Video framerates
        "Same as source" : None,
        "5" : "5",
        "10" : "10",
        "12" : "12",
        "15" : "15",
        "23.976 (NTSC Film)" : "23.976",
        "24" : "24",
        "25 (PAL Film/Video)" : "25",
        "29.97 (NTSC Video)" : "29.97",
        # Audio encoders
        "AAC (ffmpeg)" : "ffaac",
        "AAC (faac)" : "faac",
        "AAC (CoreAudio)" : "ca_aac",
        "HE-AAC (CoreAudio)" : "ca_haac",
        "AC3 (ffmpeg)" : "ac3",
        "AAC Passthru" : "copy:aac",
        "MP3 Passthru" : "copy:mp3",
        "AC3 Passthru" : "copy:ac3",
        "DTS Passthru" : "copy:dts",
        "DTS-HD Passthru" : "copy:dtshd",
        "Auto Passthru" : "copy",
        "auto" : "copy",
        "MP3 (lame)" : "lame",
        "Vorbis (vorbis)" : "vorbis",
        # Audio rates
        "Auto" : "auto",
        "22.05" : "22.05",
        # "24" : "24", Duplicat of video rate
        "32" : "32",
        "44.1" : "44.1",
        "48" : "48",
    }

    # These need a separte dictionary because of duplicate values
    # "AC3 Passthru" ...
    xmixval = {
        # Audio mixdowns
        "Mono" : "mono",
        "Stereo" : "stereo",
        "Dolby Surround" : "dpl1",
        "Dolby Pro Logic II" : "dpl2",
        "6-channel discrete" : "6ch",
        "AC3 Passthru" : "none",
        "DTS Passthru" : "none",
        "DTS-HD Passthru" : "none",
    }

    def xbool( self, opt, value):
        if value:
            return [opt]
        return None

    # Translate value to string
    def xint( self, opt, value):
        return [opt, int(value)]

    # Translate opt to string
    def xflt( self, opt, value):
        return [opt, value]

    # Pass value unchanged
    def xstr( self, opt, value):
        return [opt, value]

    # All keys.  Those that we do not process are given Null maps.
    keys = {
        "FileFormat" :               tuple(("-f", xval)),
        "ChapterMarkers" :           tuple(("-m", xbool)),
        "Mp4LargeFile" :             tuple(("-4", xbool)),
        "Mp4HttpOptimize" :          tuple(("-O", xbool)),
        "Mp4iPodCompatible" :        tuple(("-I", xbool)),

        "VideoEncoder" :             tuple(("-e", xval)),
        "lavcOption" :               tuple(("-x", xstr)),
        "x264Option" :               tuple(("-x", xstr)),
        "VideoQualitySlider" :       tuple(("-q", xflt)),
        "VideoAvgBitrate" :          tuple(("-b", xint)),
        "VideoTwoPass" :             tuple(("-2", xbool)),
        "VideoTurboTwoPass" :        tuple(("-T", xbool)),
        "VideoFramerate" :           tuple(("-r", xval)),
        "VideoFramerateVFR" :        tuple(("--vfr", xbool)),
        "VideoFrameratePFR" :        tuple(("--pfr", xbool)),
        "VideoFramerateCFR" :        tuple(("--cfr", xbool)),
        "VideoFramerateMode" :       tuple((None, None)),

        "AudioList" :                tuple((None, None)),
        "AudioTrack" :               tuple((None, None)),
        "AudioAllowMP3Pass" :        tuple((None, None)),
        "AudioAllowAACPass" :        tuple((None, None)),
        "AudioAllowAC3Pass" :        tuple((None, None)),
        "AudioAllowDTSPass" :        tuple((None, None)),
        "AudioAllowDTSHDPass" :      tuple((None, None)),
        "AudioTrackName" :           tuple(("-A", xstr)),
        "AudioEncoder" :             tuple(("-E", xval)),
        "AudioEncoderFallback" :     tuple(("--audio-fallback", xval)),
        "AudioBitrate" :             tuple(("-B", xint)),
        "AudioMixdown" :             tuple(("-6", xmixval)),
        "AudioSamplerate" :          tuple(("-R", xval)),
        "AudioTrackDRCSlider" :      tuple(("-D", xflt)),
        "AudioTrackGain" :           tuple(("--gain", xint)),

        "PictureWidth" :             tuple(("-X", xint)),
        "PictureHeight" :            tuple(("-Y", xint)),
        "PicturePAR" :               tuple((None, None)),
        "PictureDisplayWidth" :      tuple(("--display-width", xint)),
        "PictureKeepRatio" :         tuple(("--keep-display-aspect", xbool)),
        "PicturePARWidth" :          tuple(("--pixel-aspect", None)),
        "PicturePARHeight" :         tuple((None, None)),
        "PictureModulus" :           tuple(("--modulus", xint)),
        "PictureDeinterlace" :       tuple(("-d", None)),
        "PictureDecombDeinterlace" : tuple((None, None)),
        "PictureDeinterlaceCustom" : tuple((None, None)),
        "PictureDecomb" :            tuple(("-5", None)),
        "PictureDecombCustom" :      tuple((None, None)),
        "PictureDetelecine" :        tuple(("-9", None)),
        "PictureDetelecineCustom" :  tuple((None, None)),
        "PictureDenoise" :           tuple(("-8", None)),
        "PictureDenoiseCustom" :     tuple((None, None)),
        "PictureDeblock" :           tuple(("-7", None)),
        "VideoGrayScale" :           tuple(("-g", xbool)),

        "SubtitleList" :             tuple((None, None)),
        "SubtitleLanguage" :         tuple((None, None)),
        "SubtitleForced" :           tuple((None, None)),
        "SubtitleSource" :           tuple((None, None)),
        "SubtitleBurned" :           tuple((None, None)),
        "SubtitleDefaultTrack" :     tuple((None, None)),

        "UsesMaxPictureSettings" :   tuple((None, None)),
        "UsesPictureSettings" :      tuple((None, None)),
        "UsesPictureFilters" :       tuple((None, None)),
        "PictureAutoCrop" :          tuple((None, None)),
        "PictureTopCrop" :           tuple((None, None)),
        "PictureBottomCrop" :        tuple((None, None)),
        "PictureLeftCrop" :          tuple((None, None)),
        "PictureRightCrop" :         tuple((None, None)),

        "PresetDescription" :         tuple((None, None)),
        "VideoTargetSize" :           tuple((None, None)),
        "Type" :                      tuple((None, None)),
        "Folder" :                    tuple((None, None)),
        "Folder" :                    tuple((None, None)),
        "AudioEncoderActual" :        tuple((None, None)),
        "AudioTrackDescription" :     tuple((None, None)),
        "PictureLooseCrop" :          tuple((None, None)),
        "Default" :                   tuple((None, None)),
        "VideoQualityType" :          tuple((None, None)),
        "PresetBuildNumber" :         tuple((None, None)),
        "PresetName" :                tuple((None, None)),
    }

    # default options that can be ignored if present
    def_opts = {
        "-e" : "ffmpeg4",
        "-b" : "1000",
        "--modulus" : "16",
    }

    def xdict(self, opt, value, vdict):
        val = vdict.get(value)
        if val != None:
            return [opt, val]
        return None

    def xcomplex(self, preset, opt, key, value):
        # AudioList
        if key == "AudioList":
            return self.get_audio_args(preset, value)
        # PicturePAR
        elif key == "PicturePAR":
            if value == 0:
                return None
            elif value == 1:
                return ["--strict-anamorphic"]
            elif value == 2:
                return ["--loose-anamorphic"]
            elif value == 3:
                return ["--custom-anamorphic"]
        # PictureDeinterlace
        elif key == "PictureDeinterlace":
            if value == 0:
                return None
            elif value == 1:
                value = preset.get("PictureDeinterlaceCustom")
                if value != None:
                    return ["%s=%s" % (opt, value)]
            elif value == 2:
                return ["%s=%s" % (opt, "fast")]
            elif value == 3:
                return ["%s=%s" % (opt, "slow")]
            elif value == 4:
                return ["%s=%s" % (opt, "slower")]
        # PictureDecomb
        elif key == "PictureDecomb":
            if value == 0:
                return None
            elif value == 1:
                value = preset.get("PictureDecombCustom")
                if value != None:
                    return ["%s=%s" % (opt, value)]
            elif value == 2:
                return [opt]
        # PictureDetelecine
        elif key == "PictureDetelecine":
            if value == 0:
                return None
            elif value == 1:
                value = preset.get("PictureDetelecineCustom")
                if value != None:
                    return ["%s=%s" % (opt, value)]
            elif value == 2:
                return [opt]
        # PictureDenoise
        elif key == "PictureDenoise":
            if value == 0:
                return None
            elif value == 1:
                value = preset.get("PictureDenoiseCustom")
                if value != None:
                    return ["%s=%s" % (opt, value)]
            elif value == 2:
                return ["%s=%s" % (opt, "weak")]
            elif value == 3:
                return ["%s=%s" % (opt, "medium")]
            elif value == 4:
                return ["%s=%s" % (opt, "strong")]
        # PictureDeblock
        elif key == "PictureDeblock":
            if value >= 5:
                return ["%s=%d" % (opt, value)]
        # VideoFramerateMode
        elif key == "VideoFramerateMode":
            if value == "cfr":
                return ["--cfr"]
            if value == "pfr":
                return ["--pfr"]
            if value == "vfr":
                return ["--vfr"]
        return None

    def translate(self, preset, key):
        x = self.keys.get(key)
        if x == None:
            print "Unrecognized key %s" % key
            return None

        value = preset.get(key)
        if value == None:
            return None

        arg = None
        opt, xlat = x
        if opt != None and xlat != None:
            if type(xlat) == types.DictType:
                arg = self.xdict(opt, value, xlat)
            elif type(xlat) == types.FunctionType:
                arg = xlat(self, opt, value)
            else:
                print "Unrecognized xlat type", xlat
                arg = None
        else:
            arg = self.xcomplex(preset, opt, key, value)

        return arg

    def polarity_check_deps(self, polarity, dep_dict, pdict, pkey):
        deps = dep_dict.get(pkey)
        if deps == None:
            return True

        for key, values in deps:
            pval = pdict[key]
            for val in values:
                if pval == val:
                    return polarity
        return not polarity

    def checkdeps(self, pdict, key):
        return (self.polarity_check_deps(True, self.dep_dict, pdict, key) and
               self.polarity_check_deps(False, self.ndep_dict, pdict, key))

    def __init__(self, plistfile=None):
        if plistfile != None:
            self.load(plistfile)

    def load(self, plistfile):
        if os.path.exists(plistfile):
            self.plist = plistlib.readPlist(plistfile)
        else:
            print "Error: plist file (%s) not found." % plistfile

    def have_plist(self):
        return self.plist != None

    def preset(self, name, list=None):
        if list == None:
            list = self.plist
        for preset in list:
            if preset.get("Folder", False):
                p = self.preset(name, preset["ChildrenArray"])
                if p != None:
                    return p
            elif preset["PresetName"] == name:
                return preset

        return None

    def is_custom(self, name):
        preset = self.preset(name)
        if preset != None and preset["Type"] == 1:
            return True
        return False

    def get_audio_args(self, preset, alist):
        ii = 0
        enc = list()
        br = list()
        mix = list()
        sr = list()
        drc = list()
        gain = list()
        name = list()
        enc_cnt = 0
        br_cnt = 0
        mix_cnt = 0
        sr_cnt = 0
        drc_cnt = 0
        gain_cnt = 0
        name_cnt = 0
        copy_mask = list()
        if len(alist) > 0:
            if preset == None:
                print "preset is none"
            allow = preset.get("AudioAllowMP3Pass")
            if allow == None or allow == True:
                copy_mask.append("mp3")
            allow = preset.get("AudioAllowAACPass")
            if allow == None or allow == True:
                copy_mask.append("aac")
            allow = preset.get("AudioAllowAC3Pass")
            if allow == None or allow == True:
                copy_mask.append("ac3")
            allow = preset.get("AudioAllowDTSPass")
            if allow == None or allow == True:
                copy_mask.append("dts")
            allow = preset.get("AudioAllowDTSHDPass")
            if allow == None or allow == True:
                copy_mask.append("dtshd")

        for adict in alist:
            # Append defaults
            enc.append("faac")
            br.append(160)
            mix.append("dpl2")
            sr.append("auto")
            drc.append(0.0)
            gain.append(0)
            name.append("")
            for key, value in adict.items():
                if self.checkdeps(adict, key):
                    opt = self.translate(adict, key)
                    if opt != None:
                        if key == "AudioEncoder":
                            enc[ii] = opt[1]
                            enc_cnt += 1
                        if key == "AudioBitrate" and opt[1] != 160:
                            br[ii] = opt[1]
                            br_cnt += 1
                        if key == "AudioMixdown" and opt[1] != "dpl2":
                            mix[ii] = opt[1]
                            mix_cnt += 1
                        if key == "AudioSamplerate" and opt[1] != "auto":
                            sr[ii] = opt[1]
                            sr_cnt += 1
                        if key == "AudioTrackDRCSlider" and opt[1] != 0.0:
                            drc[ii] = opt[1]
                            drc_cnt += 1
                        if key == "AudioTrackGain" and opt[1] != 0:
                            gain[ii] = opt[1]
                            gain_cnt += 1
                        if key == "AudioTrackName" and len(opt[1]) > 0:
                            name[ii] = opt[1]
                            name_cnt += 1
            ii += 1
        # Choose track numbers.
        # Don't encode the same track with the same encoder twice.
        et = {}
        track = list()
        for jj in range(ii):
            t = et.get(enc[jj])
            if t == None:
                t = 1
            else:
                t += 1
            et[enc[jj]] = t
            track.append(t)

        if ii > 0:
            args = []

            if len(copy_mask) > 0:
                mask = ",".join(map(str,copy_mask))
                # if it's not the default, add it to the arg list
                if mask != "mp3,aac,ac3,dts,dtshd":
                    args.extend(["--audio-copy-mask", mask])

            tracks = ",".join(map(str,track))
            args.extend(["-a", tracks])

            encoders = ",".join(map(str,enc))
            args.extend(["-E", encoders])

            if br_cnt > 0:
                bitrates = ",".join(map(str,br))
                args.extend(["-B", bitrates])

            if mix_cnt > 0:
                mixdowns = ",".join(map(str,mix))
                args.extend(["-6", mixdowns])

            if sr_cnt > 0:
                samplerates = ",".join(map(str,sr))
                args.extend(["-R", samplerates])

            if drc_cnt > 0:
                drcs = ",".join(map(str,drc))
                args.extend(["-D", drcs])

            if gain_cnt > 0:
                gains = ",".join(map(str,gain))
                args.extend(["--gain", gains])

            if name_cnt > 0:
                names = ",".join(map(str,name))
                args.extend(["-A", names])
        else:
            args = ["-a", "none"]

        return args

    def get_args(self, name):
        preset = self.preset(name)
        if preset == None:
            return []

        args = []
        for key, value in preset.items():
            if self.checkdeps(preset, key):
                opt = self.translate(preset, key)
                if opt != None:
                    args.extend(opt)

        return args

    def get_ext(self, name):
        preset = self.preset(name)
        if preset == None:
            return "m4v"

        value = preset.get("FileFormat")
        if value != None:
            return value
        return "m4v"

class HBJob:
    instance_count = 1
    child = list([None])

    def set_instance_count(self, count):
        self.instance_count = count
        self.child = list()
        for i in range(count):
            self.child.append(None)

    def run(self, cmd, log=None):
        # Find an empty child slot
        for i in range(self.instance_count):
            if self.child[i] == None:
                break
        if i == self.instance_count:
            # No empty slots found.  This shouldn't happen
            print "Error: no instance slots available."
            return 1

        if type(cmd).__name__ == 'str':
            cmd = os.path.expanduser(cmd)
            command = cmd
        elif type(cmd).__name__ == 'list':
            cmd[0] = os.path.expanduser(cmd[0])
            command = cmd[0]
        else:
            command = cmd[0]

        if log != None:
            self.child[i] = subprocess.Popen(cmd, bufsize=-1, stderr=log)
        else:
            self.child[i] = subprocess.Popen(cmd, bufsize=-1)

        # If there is no log file, block and only allow one instance
        # so that log output isn't mixed
        if log == None:
            self.child[i].wait()
            err = self.child[i].returncode
            self.child[i] = None
            if err != None and err > 0:
                raise RuntimeError, "%s failed with exit code %d" % (os.path.basename(command), err)
            elif err == -signal.SIGINT:
                raise KeyboardInterrupt
        else:
            self.wait()

        return 0

    def poll_all(self):
        count = 0
        for i in range(self.instance_count):
            if self.child[i] != None:
                self.child[i].poll()
                err = self.child[i].returncode
                if err != None:
                    self.child[i] = None
                    count += 1
                if err != None and err > 0:
                    raise RuntimeError, "%s failed with exit code %d" % (os.path.basename(command), err)
                elif err == -signal.SIGINT:
                    raise KeyboardInterrupt
            else:
                count += 1
        # returns number of available run slots
        return count

    def wait(self):
        while True:
            if self.poll_all() > 0:
                break
            time.sleep(1)

    def wait_all(self):
        while True:
            if self.poll_all() == self.instance_count:
                break
            time.sleep(1)

    def terminate(self):
        for i in range(self.instance_count):
            if self.child[i] != None:
                self.child[i].terminate()
                self.child[i] = None


class HBBatch:
    log_dir = None
    extensions = None
    recurse = None
    ext = "m4v"
    presets = None
    job = None

    def __init__(self, src_dir=".", dst_dir=".", hb_args=[]):
        self.src_dir = src_dir
        self.dst_dir = dst_dir
        self.hb_args = ["--main-feature", "-v2"]
        self.hb_args.extend(hb_args)
        self.job = HBJob()

    def set_instance_count(self, count):
        self.job.set_instance_count(count)

    def set_regex(self):
        if self.extensions == None:
            return
        self.regex = "(.*)\.((?:"
        for ext in self.extensions[0:len(self.extensions) - 1]:
            self.regex = self.regex + ext + "|"
        self.regex = self.regex + self.extensions[len(self.extensions)-1] + "))$"

    def get_extensions(self):
        return self.extensions

    def set_extensions(self, extensions):
        self.extensions = extensions
        self.set_regex()

    def set_src(self, src_dir):
        self.src_dir = src_dir

    def set_dst(self, dst_dir):
        self.dst_dir = dst_dir

    def set_dst_ext(self, ext):
        self.ext = ext

    def set_hb_args(self, hb_args):
        self.hb_args = ["--main-feature", "-v2"]
        self.hb_args.extend(hb_args)

    def set_presets(self, presets):
        self.presets = presets

    def get_recurse(self):
        return self.recurse

    def set_recurse(self, recurse):
        self.recurse = recurse

    def set_log_dir(self, log):
        self.log_dir = log

    def get_log_dir(self):
        return self.log_dir

    def walk_files(self, root):
        prog = re.compile(self.regex)
        files = []
        dirs = []
        nodes = os.listdir(root)
        nodes.sort()
        for node in nodes:
            if node[0] == ".":
                continue
            path = os.path.join(root, node)
            if os.path.isfile(path):
                files.append(path)
            if os.path.isdir(path) and not os.path.islink(path):
                if os.path.isdir(os.path.join(path, "VIDEO_TS")):
                    files.append(path)
                elif os.path.isdir(os.path.join(path, "BDMV")):
                    files.append(path)
                else:
                    dirs.append(path)

        for f in files:
            m = prog.match(f)
            if m != None:
                yield(f)
            elif "iso" in self.extensions and os.path.isdir(f):
                yield(f)

        if self.recurse:
            for d in dirs:
                for match in self.walk_files(d):
                    yield(match)

    def run(self):
        count = 0
        for match in self.walk_files(self.src_dir):
            src_file = match
            if self.recurse:
                src_dir, base = os.path.split(match)
                recurse_dir = src_dir[len(self.src_dir):].strip(os.sep)
                dst_dir = os.path.join(self.dst_dir, recurse_dir)
            else:
                src_dir, base = os.path.split(match)
                dst_dir = self.dst_dir

            base, ext = os.path.splitext(base)
            dst_file = base + "." + self.ext
            dst_file = os.path.join(dst_dir, dst_file)
            if os.path.exists(dst_file):
                print "Destination file already exists (%s)" % dst_file
                continue

            count != 1
            cmd = [hbcli] + ["-i", src_file, "-o", dst_file] + self.hb_args
            print "\n"
            print_command(cmd)

            if dryrun:
                continue

            # create destination dir if necessary
            if not os.path.exists(dst_dir):
                try:
                    os.makedirs(dst_dir)
                except os.error:
                    print "Can not create target directory %s" % dst_dir
                    continue

            gmt = time.time()
            lt = time.localtime(gmt)

            log_path = "%s/%s %d-%02d-%02d %02d-%02d-%02d.log" % (
                        self.log_dir, base,
                        lt.tm_year, lt.tm_mon + 1, lt.tm_mday,
                        lt.tm_hour, lt.tm_min, lt.tm_sec)

            try:
                log = open(log_path, "w")
            except IOError:
                print "Error: Can not open log file %s" % log_path
                log = None

            try:
                self.job.run(cmd, log)
            except RuntimeError, err:
                print "Error: %s" % err
            except KeyboardInterrupt:
                print "Brake!"
                # HandBrakeCLI doesn't always exit cleanly
                # so give it a little shove
                time.sleep(0.5)
                self.job.terminate()
                break

        try:
            self.job.wait_all()
        except RuntimeError, err:
            print "Error: %s" % err
        except KeyboardInterrupt:
            print "Brake!"
            # HandBrakeCLI doesn't always exit cleanly
            # so give it a little shove
            time.sleep(0.5)
            self.job.terminate()

        if count == 0:
            print "No files found to process..."

        return 0

class HB:
    def show_cli_help(self):
        global hbcli
        job = HBJob()
        try:
            job.run([hbcli, "--help"])
        except RuntimeError, err:
            print "Error: %s" % err


    def main(self, argv):
        global verbose, dryrun, gui

        short_opts = "s:d:hHnre:L:I:p:"
        long_opts = ["srcdir=", "dstdir=", "help", "cli-help", "dryrun",
                    "recursive", "ext=", "log-dir=", "instances=",
                    "presets-file="]
        if gui:
            short_opts += "g"
            long_opts.append("gui")

        try:
            opts, args = getopt.gnu_getopt(argv[1:], short_opts, long_opts)

        except getopt.GetoptError:
            usage(argv[0])
            sys.exit(2)

        batch = HBBatch()
        presets = None

        use_gui = False
        for opt, arg in opts:
            if opt in ("-h", "--help"):
                usage(argv[0])
                sys.exit()
            elif opt in ("-H", "--cli-help"):
                self.show_cli_help()
            elif opt in ("-n", "--dryrun"):
                dryrun = True
            elif opt in ("-s", "--srcdir"):
                batch.set_src(arg)
            elif opt in ("-d", "--dstdir"):
                batch.set_dst(arg)
            elif opt in ("-r", "--recursive"):
                batch.set_recurse(True)
            elif opt in ("-e", "--ext"):
                batch.set_extensions(arg.rsplit(","))
            elif opt in ("-L", "--log-dir"):
                batch.set_log_dir(arg)
            elif opt in ("-I", "--instances"):
                batch.set_instance_count(int(arg))
            elif opt in ("-p", "--presets-file"):
                presets = HBPlist(arg)
            elif opt in ("-g", "--gui"):
                use_gui = True

        if use_gui:
            bhbgui = BHBGui(bhb_ui, batch, presets)
            bhbgui.run()
            sys.exit(0)

        if presets == None:
            presets = HBPlist(def_presets_plist)

        if batch.get_log_dir() == None:
            batch.set_log_dir(def_log_dir)

        if batch.get_extensions() == None:
            batch.set_extensions(def_ext.rsplit(","))

        if batch.get_recurse() == None:
            batch.set_recurse(False)

        # Check the HandBrakeCLI args for a preset option.
        # If there is one, check if it is a custom preset.
        # If it is a custom preset, use the presets plist
        # to substitute options for the custom preset.
        for optind in range(len(args)):
            opt = args[optind]
            if opt == "-Z" or opt == "--preset":
                if presets.is_custom(args[optind+1]):
                    custom = args[optind+1]
                    del args[optind+1]
                    del args[optind]
                    args[0:0] = presets.get_args(custom)
                    batch.set_dst_ext(presets.get_ext(custom))
                    break

        # Check the HandBrakeCLI args for the format option
        # If it is set, we need to modify our output filename extension
        for optind in range(len(args)):
            opt = args[optind]
            if opt == "-f" or opt == "--format":
                batch.set_dst_ext(args[optind+1])
                break

        # Make everything strings
        for ii in range(len(args)):
            args[ii] = str(args[ii])
        batch.set_presets(presets)
        batch.set_hb_args(args)
        batch.run()
        sys.stdout.flush()
        print "\nBatch Done"

if __name__ == "__main__":
    hb = HB()
    hb.main(sys.argv)

```

---

### Post by xlr8ed on 2011-07-25
Dude, that's awesome!

As far as the moving files after transcode, I can just use find -mtime to move or delete them after x amount of days.

Thanks a lot!

---

### Post by mufb74 on 2013-03-05
I am trying your pyhb.py scripts on OS X (10.8.2).  Python does not like line 43 when it tries to open ./bhb.ui.  What file is this?

Thanks for this script!

---

### Post by wildmanne39 on 2013-03-05
Old thread closed! Please start a new thread you can link to this one if you need too.
Thanks

---

