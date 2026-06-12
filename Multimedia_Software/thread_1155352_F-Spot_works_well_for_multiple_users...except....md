---
title: "F-Spot works well for multiple users...except..."
date: 2009-05-10
forum: Multimedia Software
---

### Post by justpete on 2009-05-10
v8.10 on eeePC 1000he

Latest version of F-Spot and it runs fine once I got it configured correctly.  There're two users and another 'user' folder for music and photos, each in their own folders and both set to share. Symlinks to picture folder work fine for both users but F-Spot didn't until I found a solution online to create links from the picture/music folder's F-Spot photos.db file to ~/.gnome2/f-spot/photos.db for both.

Now F-Spot launches in each user's desktop with changes made in one reflected in any other.  But both the users' Media tabs in their respective File Management pref panels have the Photos: option grayed out, only the 'user' folder where the picture files are located provides a choice, which is set to F-Stop Import.

And only in this folder will a camera connection or insertion of an SD(HC) card launch F-Spot and successfully get files for copying.  Without an auto-option in the main users' folders connection of the camera or insertion of an SD(HC) card does nothing, after having checked the box in the original popup to repeat the action in the future, the action being nothing since the option bar in the popup was grayed out, too.

Manually launching F-Spot in either user's desktop with a camera connected yields the unable to lock to device error (forgotten the exact wording but found multiple references to it online - I know it's fixed in v8.10) whether I try to select either of the USB options in the popup or cancel it and click on import and select the camera PDP option whereupon the error is issued.

In the other user's desktop as well as the 'user' desktop where the pics are stored there's a different popup annunciating an error -53 that the USB device wasn't available.

In either user's desktop the SD(HC) card causes F-spot to instantly crash with no error msgs anywhere.

I'd like to be able to have F-Spot act the same way in either user desktop as it does in the one where the pics are stored but can't figure out how to do it.  Searched for days and have not found much of anything except that the link to the photos.db file should've done it.

The folder with the pics in it has its group set to include both users as well as itself and root.  The ~/.gnome2/f-spot/* folder has its group permissions set to rw, recursively, as do those in the users'.  I'm too ignorant to know where to look for any useful info or what diagnostics I can run or where error logs would be.  Still learning, sorry for so little info but if anyone has a hint or a pointer to help me get this running I'd be most appreciative.

Thanks, Pete

---

### Post by justpete on 2009-05-10
debug and error information collected per notes below. rtfm always helps.
Not sure what I did but the crashing stopped.  Still doesn't work with the camera but does with the card directly as long as it isn't via auto-import.

-----------------------

Output from f-spot --debug in terminal w/SDHC card mounted prior to launch

Using import button dup's were recognized and only the four new images appeared in the window, as expected, which copied without error to the catalog, appearing in the F-Spot window.  F-Spot did not crash.

Running f-spot in Debug Mode **
** Running Mono with --debug   **
[Info  20:13:01.880] Initializing DBus
[Debug 20:13:02.334] DBusInitialization took 0.409949s
[Info  20:13:02.334] Initializing Mono.Addins
[Debug 20:13:03.453] Mono.Addins Initialization took 1.118933s
[Info  20:13:03.476] Starting new FSpot server
[Debug 20:13:05.132] Db Initialization took 0.619058s
[Debug 20:13:06.718] QueryToTemp took 0.118312s : SELECT id, time, uri, description, roll_id, default_version_id, rating, md5_sum FROM photos  ORDER BY  time DESC
[Debug 20:13:07.112] PhotosPerMonth took 0.063951s
[Debug 20:13:07.121] TimeAdaptor REAL Reload took 0.282719s
[Debug 20:13:07.366] Query took 0.067892s : SELECT * FROM photoquery_temp_0 LIMIT 100 OFFSET 0
[Info  20:13:07.979] Starting BeagleService
[Debug 20:13:07.983] BeagleService startup took 4.5E-05s
[Info  20:13:07.983] Hack for gnome-settings-daemon engaged
[Debug 20:13:08.418] IndexOf took 0.00651s : SELECT ROWID FROM photoquery_temp_0 WHERE time <= 1243835999 ORDER BY time DESC LIMIT 1
[Debug 20:13:08.421] IndexOf took 0.00222s : SELECT ROWID FROM photoquery_temp_0 WHERE id = 505

(f-spot:6583): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
/host (61.3 GB) - gnome-dev-harddisk - Mountpoint file:///host True True Harddrive
Harddrive
item ImportCommand+SourceItem
Testing gphoto path = usb:005,004
PortInfo Universal Serial Bus, usb:005,004
Error Lock: LibGPhoto2.GPhotoException: Could not lock the device
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context
cleanup context
[Info  20:13:55.425] Exitingarddisk - Mountpoint file:///host True True Harddrive
Harddrive
item ImportCommand+SourceItem
Testing gphoto path = usb:005,004
PortInfo Universal Serial Bus, usb:005,004
Error Lock: LibGPhoto2.GPhotoException: Could not lock the device
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context
cleanup context
[Info  20:13:55.425] Exiting

------------------------

With card mounted "f-spot-import %u" launcher ran from menu automatically picking up card and successfully detecting dup's.
When finished copying to catalog threw this error in a popup (and repeated with each click on skip) as each new image was to xfer to catalog.  F-Spot didn't crash.

Access to the path is denied.
System.UnauthorizedAccessException: Access to the path is denied.
 at System.IO.File.Move (System.String src, System.String dest) [0x00000]
 at FSpot.CameraFileSelectionDialog.SaveFile (Int32 index) [0x00000]
 at FSpot.CameraFileSelectionDialog.Download () [0x00000]

--------------------------

Maybe this will help.

Thanks, Pete

---

### Post by justpete on 2009-05-15
Resolved.

User directories apparently corrupted. Unable to find root cause but adding new users, copying, and configuring never grayed out the file management pref for photos under the media tab, etc.

---

### Post by Mash909 on 2010-08-08
I found that this error happened in the following circumstances.

Created a "shared user" instance of F-Spot.

Logged in as second new user, and imported pictures from camera using F-Spot.
This created a new directory for the day of the import of pictures having user/group ownership of the second user, and also not having group writable permissions.

After doing this, I couldn't import pictures as the original user ("Access to the path is denied" error)

Solution was to recursively chmod and chown the newly created directories by the second user back to the first user.

Import as the first user was fine after doing this.

From now on, will stick to importing as the first user only.

---

