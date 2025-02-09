# KSP_PartVolume 

This is a small mod which will add the `ModuleCargoPart` to all parts which don't already have it.  This is
necessary in order to allow a part to be an inventory cargo part that can be placed in inventories or allowing 
larger parts to be manipulated in EVA construction mode (but not placeable in inventories).

It works by using the stock method `GetRendererBounds()` to get the outermost bounds of the part.

## Install

You also need to install following mods for this mod to work:
 - SpaceTuxLibrary
 - 000_ClickThroughBlocker
 - 001_ToolbarControl

## Usage

Install the mod using either CKAN or a manual install. 
The first time the game is run, a file will be created in the GameData directory called `partVolume.cfg`
A popup warning will be shown indicating that the file has been generated and the game will need to be restarted for it to take effect.

## Settings

A toolbar button will be visible when at the MainMenu.  Click the button to open a Settings window

Filler is a default amount of extra volume used for packing and storage.  There are several different filler settings, the settings are (with their defaults) as follows:

## Part Type

	RCS Filler (20%)					Filler for RCS parts
	DoTanks (False)						Create configs for tanks
	Manned (False)						Create configs for manned parts
	Stock (False)						Create configs for stock parts
	Filler	(10%)						A default amount when no other applies
	ScienceFiller (25%)					Filler for science parts
	EngineFiller (15%)					Filler for engines
	Limit Size (True)					Limit maximum size for a config to be applied (before filler adjustment)
	Largest Allowable Part (64000 l)			Largest volume allowed if Limit Size is true

All filler percentages go from 0 to 100%.  In the event that more than one type of filler can apply to a part, only the largest will apply.

Part types are determined as follows:

	Science		Part is listed in the config to be a PartCategories.Science part
	Engine		Part has either ModuleEngines or ModuleEnginesFX
	RCS		Part has either ModuleRCS or ModuleRCSFX
	Tank		Part has resources and no other module (yes, this includes batteries)
	Manned		Part can hold crew

If any setting is changed and saved, the config file (`GameData/partVolumes.cfg`) is deleted and a popup is shown indicating that the game will need to be restarted


All configs generated by this mod will only apply if a part does NOT have a `ModuleCargoPart` already defined.  This way mods can get updated by the author with their settings with no worry that their settings will be overridden.

If you have *Kerbal Inventory For All* installed, you will need to delete the file:


     GameData/KerbalInventoryForAll/AllowModPartsInStock.cfg


Whitelist
	Parts can be added to a whitelist, to allow parts which would normally not be processed (such as stock) to be processed on a per-part basis

Blacklist
	Parts can be excluded by adding to a blacklist

The blacklist and whitelist can be in the same file, and there can be multiple files.

