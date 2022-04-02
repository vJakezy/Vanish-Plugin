package net.exemplarnetwork;
 
import org.bukkit.Bukkit;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import org.bukkit.plugin.java.JavaPlugin;
 
import net.md_5.bungee.api.ChatColor;
 
public class VanishPlugin extends JavaPlugin{
    
    @Override
    public void onEnable() {
        this.getLogger().info(ChatColor.GREEN + "Vanish plugin is enabled!");
    }
    
    @Override
    public void onDisable() {
        this.getLogger().info(ChatColor.GREEN + "Vanish plugin is disabled!");
    }
    
    public boolean onCommand(CommandSender sender, Command command, String label, String[] args){
        
        Player player = (Player) sender;
        
        if (command.getName().equalsIgnoreCase("vanish") && sender instanceof Player) {
            if (sender instanceof Player){
                if (args.length == 0) {
                    player.sendMessage (ChatColor.RED + "Please specify a player name!");
                    return true;
            }
            Player target = Bukkit.getServer().getPlayer(args[0]);
            
            if (target == null) {
                player.sendMessage(ChatColor.RED + "Could not find player " + args[0] + "!");
                return true;
            }
            
            player.hidePlayer(player);      
    
            }
        }
        
        if (command.getName().equalsIgnoreCase("unvanish")) {
            if (sender instanceof Player) {
                if (args.length == 0) {
                    player.sendMessage(ChatColor.RED + "Please specify a player name!");
                    return true;
                }
                Player target = Bukkit.getServer().getPlayer(args[0]);
                
                if (target == null) {
                    player.sendMessage(ChatColor.RED + "Could not find player " + args[0] + "!");
                    return true;
                }
                
                player.showPlayer(player);
                
            }
            
        }
        return true;
    }
}
