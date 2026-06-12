---
title: "gphoto2 and camera verses Sony Memory Sticks  (oops)"
date: 2008-02-17
forum: Multimedia Production
---

### Post by none-letmebe on 2008-02-17
Evening all,

The 'why won't a camera automatically download with Ubuntu 7.1 mystery' is almost over.   The Canon camera (over USB) on my Sony Vaio SZ laptop worked with 7.04 flawlessly.   

Why not now:  This is because 7.10 recognises the Sony Memory Stick and 7.04 did not.  Unfortunately, one has to disable or remember to unmount the memory stick afore one inserts the camera.

If you do not unmount  the Sony Memory Stick then gphoto2 picks the Memory Stick up first instead of the camera.  This will cause a problem when Gnome autodetects a camera being attached to the computer because it won't detect the camera ; gphoto2 is not launched.  If one unmounts the Memory Stick and then inserts the camera then gphoto2 is called. 

However, --get-all-files is a cockup (my mistake here)  because it dumps these all into the home directory and nor does it offer any notification of progress.  The only options is to run a ps -eaf|grep gphoto2 and watch for the programme is finish.

Gphoto2 also looses all the file data:
I now have three hundreds files in my home directory and have no idea on  which date these were taken.  Canon's bundled camera software takes care of this.  Has anyone got this working with Wine or found something a little more elegant than gphoto2.

--------------------------------------------------------------------------------------------------------------------
 gphoto2 --summary will fail with something like this:

$ gphoto2 --summary
                                                                              
*** Error ***             
This camera does not support summaries.
*** Error (-6: 'Unsupported operation') ***      

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --summary

Please make sure there is sufficient quoting around the arguments
                         
Feb 17 19:40:24 axe kernel: [ 4656.852000] usb 5-3: configuration #1 chosen from 1 choice
Feb 17 19:42:19 axe kernel: [ 4771.720000] usb 5-3: USB disconnect, address 8
Feb 17 19:42:31 axe kernel: [ 4783.500000] tifm0 : demand removing card from socket 0:0
Feb 17 19:42:45 axe kernel: [ 4797.344000] tifm_core: MemoryStick card detected in socket 0:0
Feb 17 19:42:45 axe kernel: [ 4797.424000]  mspblk0: p1
Feb 17 19:43:35 axe kernel: [ 4847.704000] tifm0 : demand removing card from socket 0:0
Feb 17 19:43:39 axe kernel: [ 4851.420000] tifm_core: MemoryStick card detected in socket 0:0
Feb 17 19:43:39 axe kernel: [ 4851.500000]  mspblk0: p1
Feb 17 19:43:51 axe kernel: [ 4863.224000] usb 5-3: new high speed USB device using ehci_hcd and address 9
Feb 17 19:43:51 axe kernel: [ 4863.388000] usb 5-3: configuration #1 chosen from 1 choice

--------------------------------------------------------------------------------------------------------------------
After Sony Memory Stick is removed:
$ gphoto2 --summary
Camera summary:                                                               
Model: Canon EOS 400D DIGITAL
  device version: 3-1.1.1
  serial number:  0000000000000000000000007020047e
Vendor extension ID: 0x0000000b
Vendor extension description: (null)

Capture Formats: JPEG
Display Formats: Association/Directory, Script, MS AVI, MS Wave, JPEG, CRW, Unknown(b103), Unknown(bf02), Defined Type

Device Capabilities:
        File Download, File Deletion, File Upload
        No Image Capture, No Open Capture, No vendor specific capture

Storage Devices Summary:
store_00010001:
        StorageDescription: CF
        VolumeLabel:
        Storage Type: Removable RAM (memory card)
        Filesystemtype: Digital Camera Layout (DCIM)
        Access Capability: Read-Write
        Maximum Capability: 2039545856 (1945 MB)
        Free Space (Bytes): 707624960 (674 MB)
        Free Space (Images): -1

Device Property Summary:
Event Emulate Mode(0xd045):(readwrite) (type=0x4) Enumeration [1,2,3,4,5,6,7] value: 2
Property 0xd402:(read only) (type=0xffff) 'Canon EOS 400D DIGITAL'
Property 0xd407:(read only) (type=0x6) 1
Property 0xd406:(readwrite) (type=0xffff) 'Unknown Initiator'
Model ID(0xd049):(read only) (type=0x6) 2147484214
Property 0xd04a:(readwrite) (type=0x2) Enumeration [0,1,2,3] value: 0

gphoto2: {/home/fred} /> ls
store_00010001/     
gphoto2: {/home/fred} /> cd store_00010001/
Remote directory now '/store_00010001'.
gphoto2: {/home/fred} /store_00010001> cd DCIM/132CANON
Remote directory now '/store_00010001/DCIM/132CANON'.
gphoto2: {/home/fred} /store_00010001/DCIM/132CANON> ls
      
IMG_3699.JPG        IMG_3704.JPG        IMG_3705.JPG        IMG_3707.JPG         IMG_3821.CR2       
gphoto2: {/home/fred} /store_00010001/DCIM/132CANON> show-exif IMG_3821.CR2
Downloading 'IMG_3821.CR2' from folder '/store_00010001/DCIM/132CANON'...
Downloading 'IMG_3821.CR2' from folder '/store_00010001/DCIM/132CANON'...
EXIF tags:
--------------------+-----------------------------------------------------------
Tag                 |Value                                                      
--------------------+-----------------------------------------------------------
--------------------+-----------------------------------------------------------
gphoto2: {/home/fred} /store_00010001/DCIM/132CANON> show-info IMG_3821.CR2
Information on file 'IMG_3821.CR2' (folder '/store_00010001/DCIM/132CANON'):
File:
  Name:        'IMG_3821.CR2'
  Mime type:   'application/x-unknown'
  Size:        9912966 byte(s)
  Time:        Sat Feb  9 16:47:02 2008
Thumbnail:
  None available.
Audio data:
  None available.
gphoto2: {/home/fred} /store_00010001/DCIM/132CANON> show-exif IMG_3705.JPG
Downloading 'IMG_3705.JPG' from folder '/store_00010001/DCIM/132CANON'...
EXIF tags:
--------------------+-----------------------------------------------------------
Tag                 |Value                                                      
--------------------+-----------------------------------------------------------
Make                |Canon                                                      
Model               |Canon EOS 400D DIGITAL                                     
Orientation         |right - top                                                
XResolution         |72.00                                                      
YResolution         |72.00                                                      
ResolutionUnit      |Inch                                                       
DateTime            |2008:01:26 15:24:38                                        
YCbCrPositioning    |co-sited                                                   
ExposureTime        |1/199 sec.                                                 
FNumber             |f/9.0                                                      
ExposureProgram     |Normal program                                             
ISOSpeedRatings     |400                                                        
ExifVersion         |Exif Version 2.21                                          
DateTimeOriginal    |2008:01:26 15:24:38                                        
DateTimeDigitized   |2008:01:26 15:24:38                                        
ComponentsConfigurat|Y Cb Cr -                                                  
ShutterSpeedValue   |7.64 EV (APEX: 14, 1/200 sec.)                             
ApertureValue       |6.34 EV (f/9.0)                                            
ExposureBiasValue   |0.00 EV                                                    
MeteringMode        |Pattern                                                    
Flash               |Flash did not fire, compulsory flash mode.                 
FocalLength         |21.0 mm                                                    
MakerNote           |4876 bytes unknown data                                    
UserComment         |                                                           
FlashPixVersion     |FlashPix Version 1.0                                       
ColorSpace          |sRGB                                                       
PixelXDimension     |3888                                                       
PixelYDimension     |2592                                                       
FocalPlaneXResolutio|4433.30                                                    
FocalPlaneYResolutio|4453.61                                                    
FocalPlaneResolution|Inch                                                       
CustomRendered      |Normal process                                             
ExposureMode        |Auto exposure                                              
WhiteBalance        |Auto white balance                                         
SceneCaptureType    |Standard                                                   
InteroperabilityInde|R98                                                        
InteroperabilityVers|0100                                                       
--------------------+-----------------------------------------------------------


Best wishes, Let.

---

