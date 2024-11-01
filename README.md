# twoSpaceTabs

I work at a company where they prefer four space tabs.
I prefer two-space tabs for personal projects.

I don't like to menu-dive to change this, so here's a quick script to run
to change your Xcode settings


```
import plistlib

# Path to your plist file
plist_path = '~/Library/Preferences/com.apple.dt.Xcode.plist'

# Expand the user directory symbol (~)
import os
plist_path = os.path.expanduser(plist_path)

# Read the current plist file
with open(plist_path, 'rb') as fp:
    plist = plistlib.load(fp)

# Modify the relevant keys
plist['DVTTextIndentTabWidth'] = 2
plist['DVTTextIndentWidth'] = 2
plist['DVTTextWrappedLinesIndentWidth'] = 2

# Write the changes back to the plist file
with open(plist_path, 'wb') as fp:
    plistlib.dump(plist, fp)

print(f"Modified {plist_path} successfully!")

```