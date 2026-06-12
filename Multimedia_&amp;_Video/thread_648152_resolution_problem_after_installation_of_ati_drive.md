---
title: "resolution problem after installation of ati driver 8.44.3"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by zhouxing on 2007-12-23
[http://ubuntuforums.org/showthread.php?t=647311](http://ubuntuforums.org/showthread.php?t=647311)

Please see the detail of the problem from above thread.

---

### Post by zhouxing on 2007-12-23
Print


December 19, 2007

    AMD Proprietary Linux Release Notes

    This release note provides information on the latest posting of AMD's Proprietary Linux driver. This particular driver updates the software version to 8.443.
    	Caution: 	This release of the AMD Proprietary Linux driver no longer supports XFree86 4.3 or Linux Kernel 2.4

    The AMD Linux release notes provides information on the following:

        * Web Content
        * ATI Workstation Product Support
        * ATI Mobility™ and Integrated Product Family Support
        * ATI Desktop and Integrated Product Family Support
        * Operating Systems Distributions Supported
        * System Requirements
        * New Features
        * Resolved Issues
        * Known Issues
        * Installing the AMD Proprietary Linux Software Driver
        * Driver Update Notification
        * AMD Customer Care
        * Linux Feedback Program 

    Web Content

    The ATI Catalyst™ Linux Graphics Driver software suite is available through an Installer executable.
    	Note: 	Refer to the minimum system requirements listed below to ensure you have downloaded the correct driver package for your system.
    ATI Workstation Product Support

    The ATI Catalyst™ Linux software suite is designed to support the following ATI Workstation products:
    FireGL™ V8650
    	FireGL™ V5000
    	FireGL™ X2-256
    FireGL™ V8600
    	FireGL HD3870
    	FireGL™ Z1-128
    FireGL™ V7600
    	FireGL HD3850
    	FireGL™ T2-128
    FireGL™ V7350
    	FireGL™ V3600
    	FireGL™ X1-128
    FireGL™ V7300
    	FireGL™ V3400
    	FireGL™ X1-256p
    FireGL™ V7200
    	FireGL™ V3300
    	FireMV™ 2200 (Single card PCI-e configuration)
    FireGL™ V7100
    	FireGL™ V3200
    	Mobility™ FireGL™ V5000
    FireGL™ V5600
    	FireGL™ V3100
    	Mobility™ FireGL™ T2
    FireGL™ V5200
    	FireGL™ X3-256
    	

    FireGL™ V5100
    	FireGL™ X3
    	

    ATI Mobility™ and Integrated Product Family Support

    The ATI Catalyst™ Linux software suite is designed to support the following ATI Mobility™ products:
    Mobility™ Radeon™ X1800
    	Mobility™ Radeon™ X600
    Mobility™ Radeon™ X1600
    	Mobility™ Radeon™ X300
    Mobility™ Radeon™ X1400
    	Mobility™ Radeon™ X200
    Mobility™ Radeon™ X1300
    	Mobility™ Radeon™ 9800
    Mobility™ Radeon™ X1200
    	Mobility™ Radeon™ 9600
    Mobility™ Radeon™ X1100
    	Mobility™ Radeon™ 9550
    Mobility™ Radeon™ X800
    	Mobility™ Radeon™ 9500
    Mobility™ Radeon™ X700
    	Mobility™ Radeon™ Xpress 1100 series
    Mobility™ Radeon™ Xpress 1200 series
    	Mobility™ Radeon™ Xpress 200 series
    ATI Desktop and Integrated Product Family Support

    The ATI Catalyst™ Linux software suite is designed to support the following ATI desktop products:
    Radeon™ HD 2900 series
    	Radeon™ Xpress1200 series
    Radeon™ HD 2400 series
    	Radeon™ Xpress 200 series
    Radeon™ HD 2600 series
    	Radeon™ X600 series
    Radeon™ X1900 series
    	Radeon™ X550/X300 series
    Radeon™ X1800 series
    	Radeon™ 9800 series
    Radeon™ X1600 series
    	Radeon™ 9700 series
    Radeon™ X1300 series
    	Radeon™ 9600 series
    Radeon™ X850 series
    	Radeon™ 9550 series
    Radeon™ X800 series
    	Radeon™ 9500 series
    Radeon™ X700 series
    	Radeon™ Xpress 1100 series
    	Note: 	All-In-Wonder™ variants based on the above are also supported. Video capture however is not supported.
    	Note: 	Software driver support for ATI FireGL™, Integrated, Mobility™ and Desktop products prior to the Radeon™ 9500 is available from ati.com

    Operating Systems Distributions Supported

    The latest version of the ATI Catalyst™ Linux software suite is designed to support the following Linux distributions:

        * Red Hat Enterprise Linux suite
        * Novell/SuSE product suite

    	Note: 	The ATI Catalyst™ Linux software suite may install on a number of other Linux distributions. Refer to the Package Generation installation instructions for more information.
    	Note: 	AMD has accepted contributed packaging scripts to allows creation of other packages, but does not necessarily test, verify or warrant the reliability. Currently Red Hat Enterprise Linux suite and Novell/SuSE product suite are supported Linux distributions
    System Requirements

    Before attempting to install the ATI Catalyst™ Linux software suite, the following software must be installed:

        * XOrg 6.7, 6.8, 6.9, 7.0, 7.1, 7.2 or 7.3
        * Linux Kernel 2.6 and above
        * glibc version 2.2 or 2.3
        * POSIX Shared Memory (/dev/shm) support is required for 3D applications

    	Caution: 	The ATI Catalyst™ Linux software suite 8.42.3 will be the final software suite that supports Linux kernel 2.4 and XFree86 version 4.3

    The ATI Catalyst™ Linux software suite no longer provides precompiled Kernel Modules; all installations require GCC compiler and kernel-headers or kernel-source in order to enable 2D and 3D acceleration.

    For best performance and ease of use, AMD recommends the following:

        * Kernel module build environment - should include the following:
              o Kernel source code: Either the Kernel Source or Kernel Headers packages 
        * The rpm utility should be installed and configured correctly on your system, if you intend to install via RPM packages 

    The following packages must be installed in order for the ATI Catalyst™ Linux driver to install and work properly:

        * XFree86-Mesa-libGL
        * libstdc++
        * libgcc
        * XFree86-libs
        * fontconfig
        * freetype
        * zlib 

    New Features

    This release of the ATI Catalyst™ Linux driver introduces support for the following new operating systems:

        * Red Flag DT 6.0 Support
        * OpenSUSE 10.3 support 

    Resolved Issues

    The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include:

        * A memory leak is no longer noticed when running OpenGL applications
        * Running X -configure no longer results in a segmentation fault in the fglrx driver
        * fglrxinfo no longer reports OpenGL Render string: as Mesa GLX Indirect on systems containing an ATI Rialto AGP series of product 

    Known Issues

    The following section provides a brief description of known issues associated with the latest version of ATI Catalyst™ Linux software suite. These issues include:

        * There is no support for video playback on the second head in dual head mode. Further details can be found in topic number 737-26985
        * Desktop corruption may be noticed when dragging the overlay/video when using dual-display mode. Further details can be found in topic number 737-29578
        * A black screen may be observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used. Further details can be found in topic number 737-30687
        * Corruption may be noticed in the lower right corner of the display after the system is running for a long period of time
        * Display flicker may be noticed when the gnome screen-saver starts
        * Diagonal tearing may be noticed when playing a video file using a video player that utilizes the XVideo extension
        * Video playback may look blocky when playing a video file using a video player that utilizes the XVideo extension
        * Video Playback may display wrong colors and additional shadow images when cropping or expanding a video file using a video player that utilizes the XVideo extension
        * Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available
        * Custom mode lines in xorg.conf may be ignored by the fglrx driver
        * Building RPM packages for Mandriva may fail 

    For further information and general help on driver or software installation, game issues, and more, visit the ATI FAQ website.
    Installing the AMD Proprietary Linux Software Driver

    Installation information can be found at: [www.ati.com/install](www.ati.com/install)
    Driver Update Notification

    To receive driver notifications, add the following RSS feed to your RSS reader: [http://www.ati.com/online/rss/atilinuxdriver.rss](http://www.ati.com/online/rss/atilinuxdriver.rss)
    	Note: 	In order to receive notifications you will need to have an RSS reader installed.

    AMD Customer Care

    The AMD Customer Care website provides a high level of technical support and easy of navigation. The AMD Customer Care website provides accurate and up-to-date product support for optimum usability and performance. Technical issues are categorized and personalized to enhance user experience. The AMD Customer Care Website can be found at: support.ati.com

    To view a known or resolved issue, do the following:

       1. Go to: support.ati.com. The AMD Customer Care web page is displayed.
       2. In the top left hand pane, click Advanced Search. The Advanced Search pane is displayed.
       3. Under Search Type: Select the By: ID option.
       4. Enter the Topic number.
       5. Click Go. 

    Linux Feedback Program

    The ATI Catalyst™ Linux software suite releases may incorporate suggestions received through the Linux feedback program.
    Please refer to [http://apps.ati.com/linuxDfeedback/](http://apps.ati.com/linuxDfeedback/) to provide us with feedback.
    New Copyrights, Redistribution notice, and Disclaimers

    Copyright (C) 1999 Serika Kurusugawa. All rights reserved.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS". ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    - Shift-JIS Text Codec

    - ISO 2022-JP (JIS) Text Codec

    - EUC-JP Text Codec

    --------------------------------------------------------------------------------

    Copyright (C) 1999-2000 Mizi Research Inc. All rights reserved.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    - EUC-KR Text Codec

    --------------------------------------------------------------------------------

    Copyright (C) 2000 TurboLinux, Inc. Written by Justin Yu and Sean Chen.

    Copyright (C) 2001, 2002 Turbolinux, Inc. Written by James Su.

    Copyright (C) 2001, 2002 ThizLinux Laboratory Ltd. Written by Anthony Fok.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    - GBK Text Codec

    --------------------------------------------------------------------------------

    Copyright (C) 2000 Ming-Che Chuang

    Copyright (C) 2001, 2002 James Su, Turbolinux Inc.

    Copyright (C) 2002 WU Yi, HancomLinux Inc.

    Copyright (C) 2001, 2002 Anthony Fok, ThizLinux Laboratory Ltd.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    Big5-HKSCS Text Codec

    --------------------------------------------------------------------------------

    Copyright (C) 2000 Ming-Che Chuang

    Copyright (C) 2002 James Su, Turbolinux Inc.

    Copyright (C) 2002 Anthony Fok, ThizLinux Laboratory Ltd.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    Big5 Text Codec

    --------------------------------------------------------------------------------

    Copyright (C) 2005 Trolltech AS. All rights reserved.

    Copyright (C) 2005 Bjoern Bergstroem

    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, modify, market, reproduce, grant sublicenses and distribute subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. These files are provided AS IS with NO WARRANTY OF ANY KIND, INCLUDING THE WARRANTY OF DESIGN, MERCHANTIBILITY AND FITNESS FOR A PARTICULAR PURPOSE.

    Implementation of the Recursive Shadow Casting Algorithm in Qt Designer

    --------------------------------------------------------------------------------

    Copyright (C) 2005 Trolltech AS. All rights reserved.

    Copyright (C) 2005 Roberto Raggi

    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, modify, market, reproduce, grant sublicenses and distribute subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. These files are provided AS IS with NO WARRANTY OF ANY KIND, INCLUDING THE WARRANTY OF DESIGN, MERCHANTIBILITY AND FITNESS FOR A PARTICULAR PURPOSE.

    Contributions to the Following Qt Designer Files: treewalker.h, treedump.cpp, treedump.h, treewalker.cpp

    --------------------------------------------------------------------------------

    Copyright (c) 1989 The Regents of the University of California. All rights reserved.

    Redistribution and use in source and binary forms are permitted provided that the above copyright notice and this paragraph are duplicated in all such forms and that any documentation, advertising materials, and other materials related to such distribution and use acknowledge that the software was developed by the University of California, Berkeley. The name of the University may not be used to endorse or promote products derived from this software without specific prior written permission. THIS SOFTWARE IS PROVIDED "AS IS" AND WITHOUT ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, WITHOUT LIMITATION, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.

    - QDate::weekNumber()

    --------------------------------------------------------------------------------

    Copyright (c) 1991 by AT&T.

    Permission to use, copy, modify, and distribute this software for any purpose without fee is hereby granted, provided that this entire notice is included in all copies of any software which is or includes a copy or modification of this software and in all copies of the supporting documentation for such software.

    THIS SOFTWARE IS BEING PROVIDED "AS IS", WITHOUT ANY EXPRESS OR IMPLIED WARRANTY. IN PARTICULAR, NEITHER THE AUTHOR NOR AT&T MAKES ANY REPRESENTATION OR WARRANTY OF ANY KIND CONCERNING THE MERCHANTABILITY OF THIS SOFTWARE OR ITS FITNESS FOR ANY PARTICULAR PURPOSE.

    This product includes software developed by the University of California, Berkeley and its contributors.

    - QLocale

    --------------------------------------------------------------------------------

    Copyright (c) 2000 Hans Petter Bieker. All rights reserved.

    Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

    2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    - TSCII Text Codec

    --------------------------------------------------------------------------------

    Copyright (c) 2002 Jorge Acereda and Peter O'Gorman.

    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

    - QPluginLoader::load()

    - QLibrary::load()

    - QLibrary::resolve()

    --------------------------------------------------------------------------------

    Copyright 1995, Trinity College Computing Center.

    Written by David Chappell.

    Permission to use, copy, modify, and distribute this software and its documentation for any purpose and without fee is hereby granted, provided that the above copyright notice appear in all copies and that both that copyright notice and this permission notice appear in supporting documentation. This software is provided "as is" without express or implied warranty.

    TrueType font support. These functions allow PPR to generate PostScript fonts from Microsoft compatible TrueType font files.

    The functions in this file do most of the work to convert a TrueType font to a type 3 PostScript font.

    Most of the material in this file is derived from a program called "ttf2ps" which L. S. Ng posted to the usenet news group "comp.sources.postscript". The author did not provide a copyright notice or indicate any restrictions on use.

    Last revised 11 July 1995.

    - QPrinter

    --------------------------------------------------------------------------------

    Copyright 1996 Daniel Dardailler.

    Permission to use, copy, modify, distribute, and sell this software for any purpose is hereby granted without fee, provided that the above copyright notice appear in all copies and that both that copyright notice and this permission notice appear in supporting documentation, and that the name of Daniel Dardailler not be used in advertising or publicity pertaining to distribution of the software without specific, written prior permission. Daniel Dardailler makes no representations about the suitability of this software for any purpose. It is provided "as is" without express or implied warranty.

    Modifications Copyright 1999 Matt Koss, under the same license as above.

    - Drag and Drop

    --------------------------------------------------------------------------------

    Qt supports GIF reading if it is configured that way during installation. If it is, we are required to state that "The Graphics Interchange Format(c) is the Copyright property of CompuServe Incorporated. GIF(sm) is a Service Mark property of CompuServe Incorporated."

    Warning: If you are in a country that recognizes software patents and in which Unisys holds a patent on LZW compression and/or decompression and you want to use GIF, Unisys may require you to license that technology. Such countries include Canada, Japan, the US, France, Germany, Italy and the UK.

    GIF support may be removed completely in a future version of Qt. We recommend using the MNG or PNG format.

    - QImageReader

    --------------------------------------------------------------------------------

    Portions of this software are copyright © 1996-2002 The FreeType

    Project ([www.freetype.org](www.freetype.org)). All rights reserved.

    - Freetype2

    --------------------------------------------------------------------------------

    Copyright (C) 1995-2005 Jean-loup Gailly and Mark Adler

    This software is provided 'as-is', without any express or implied

    warranty. In no event will the authors be held liable for any damages

    arising from the use of this software.

    Permission is granted to anyone to use this software for any purpose,

    including commercial applications, and to alter it and redistribute it

    freely, subject to the following restrictions:

    1. The origin of this software must not be misrepresented; you must not

    claim that you wrote the original software. If you use this software

    in a product, an acknowledgment in the product documentation would be

    appreciated but is not required.

    2. Altered source versions must be plainly marked as such, and must not be

    misrepresented as being the original software.

    3. This notice may not be removed or altered from any source distribution.

    Jean-loup Gailly [email]jloup@gzip.org[/email]

    Mark Adler [email]madler@alumni.caltech.edu[/email]

    - Zlib

    --------------------------------------------------------------------------------

    Copyright (c) 1998, 1999, 2000 Thai Open Source Software Center Ltd

    and Clark Cooper

    Copyright (c) 2001, 2002, 2003, 2004, 2005, 2006 Expat maintainers.

    Permission is hereby granted, free of charge, to any person obtaining

    a copy of this software and associated documentation files (the

    "Software"), to deal in the Software without restriction, including

    without limitation the rights to use, copy, modify, merge, publish,

    distribute, sublicense, and/or sell copies of the Software, and to

    permit persons to whom the Software is furnished to do so, subject to

    the following conditions:

    The above copyright notice and this permission notice shall be included

    in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,

    EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF

    MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

    IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY

    CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,

    TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE

    SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

    - Expat

    --------------------------------------------------------------------------------

Advanced Micro Devices Inc.
[http://ati.amd.com](http://ati.amd.com)
Voice: (905) 882-2600
Fax: (905) 882-2620

---

