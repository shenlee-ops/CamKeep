# CamKeep

CamKeep is a portable Windows webcam settings editor built with the Logitech C920 in mind. Adjust exposure, focus, white balance, or other controls your camera exposes, then save one camera profile. At sign-in, CamKeep can restore that profile and exit. The included EXE runs on x64 Windows without an installer or G HUB.

## Quick start

1. Extract the ZIP and keep `CamKeep.exe` in a permanent folder.
2. Open the EXE and select your webcam. If you connected it after opening CamKeep, click **Refresh**.
3. Choose a setting and adjust the slider. For a manual value, clear **Auto** if available. Click **Test setting** to try the change on the camera.
4. Enable **Restore at Windows sign-in** if desired, then click **Save profile**. You can now close CamKeep.

## Low-light compensation

To keep the camera from lowering its frame rate to brighten a dim scene, clear **Low-light compensation** and click **Save profile**. The image may look darker. CamKeep reads the switch back from the driver to confirm the change.

If the toggle requires auto exposure, select **Exposure**, check **Auto**, and click **Test setting**. If the toggle shows **unavailable**, CamKeep could not read it from the current camera driver. Controls vary by device.

## Profile and startup

CamKeep stores the selected camera and its settings in `%LOCALAPPDATA%\CamKeep\profile.json`. Saving a different camera replaces the previous profile.

With restore enabled, a per-user Windows startup entry launches `CamKeep.exe --restore` at sign-in. It retries briefly if the camera is unavailable, then exits. If you move the EXE, launch it from its new location and save the profile again to update the startup path.

To remove CamKeep, clear **Restore at Windows sign-in** and click **Save profile** before deleting the EXE. You can also delete the profile folder to remove the saved settings.

## Build from source

The source is in `cam/` and uses the Go standard library and Windows APIs. With Go installed, run these commands in PowerShell from the repository root to build the x64 GUI executable.
