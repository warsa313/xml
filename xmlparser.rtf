{\rtf1\ansi\ansicpg1252\cocoartf2709
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 import os\
import xml.etree.ElementTree as ET\
\
def strip_namespace_from_tag(tag):\
    """Garde le namespace intact, mais enl\'e8ve les pr\'e9fixes de namespace."""\
    if '\}' in tag:\
        return tag.split('\}', 1)[1]  # Garde le namespace mais retire le pr\'e9fixe\
    return tag\
\
def find_element_by_xpath(root, xpath):\
    """\
    Recherche un \'e9l\'e9ment XML en tenant compte du namespace dans le chemin XPath.\
    Le namespace est identifi\'e9 et retir\'e9 dans cette recherche.\
    """\
    elements = xpath.split('/')\
    current_element = root\
    for el in elements:\
        if el:\
            # Recherche l'\'e9l\'e9ment en tenant compte du namespace\
            for child in current_element:\
                # Strip namespace to match the tag correctly\
                if strip_namespace_from_tag(child.tag) == strip_namespace_from_tag(el):\
                    current_element = child\
                    break\
            else:\
                current_element = None\
                break\
    return current_element\
\
def remove_namespace_prefixes(elem):\
    """Supprime uniquement les pr\'e9fixes de namespace, mais garde le namespace implicite."""\
    for el in elem.iter():\
        el.tag = strip_namespace_from_tag(el.tag)\
\
def update_fields_in_folder(folder_path, field_paths, base_value="StressTestEBS", start_value=1, output_folder=None, num_duplicates=1):\
    """\
    Parcourt tous les fichiers XML, modifie les champs, duplique les fichiers et sauvegarde avec des noms uniques.\
    \
    Args:\
        folder_path (str): Chemin du dossier contenant les fichiers XML.\
        field_paths (list): Liste des chemins XPath des champs \'e0 modifier.\
        base_value (str): Base de la nouvelle valeur (par d\'e9faut "StressTestEBS").\
        start_value (int): Valeur de d\'e9part pour l'incr\'e9mentation.\
        output_folder (str): Chemin vers le dossier de sortie. Si None, les fichiers sont enregistr\'e9s dans le dossier source.\
        num_duplicates (int): Nombre de duplications souhait\'e9es pour chaque fichier XML.\
    """\
    if output_folder is None:\
        output_folder = folder_path\
    if not os.path.exists(output_folder):\
        os.makedirs(output_folder)\
\
    # Liste tous les fichiers dans le dossier\
    for file_name in os.listdir(folder_path):\
        file_path = os.path.join(folder_path, file_name)\
\
        # V\'e9rifie si c'est un fichier XML\
        if os.path.isfile(file_path) and file_name.endswith('.xml'):\
            print(f"Traitement du fichier : \{file_name\}")\
\
            try:\
                # Charge le fichier XML\
                tree = ET.parse(file_path)\
                root = tree.getroot()\
\
                for duplicate_num in range(1, num_duplicates + 1):\
                    # Incr\'e9mente \'e0 chaque duplication\
                    count = start_value + duplicate_num - 1\
\
                    # Modifie les champs sp\'e9cifi\'e9s dans la liste field_paths\
                    for field_path in field_paths:\
                        field_elem = find_element_by_xpath(root, field_path)\
                        if field_elem is not None:\
                            xpath_as_string = field_path.replace('/', '_').replace('.', '')\
                            new_value = f"\{base_value\}\{xpath_as_string\}-\{count:011d\}"\
                            field_elem.text = new_value\
                            print(f"Champ modifi\'e9 : \{field_path\} -> \{new_value\}")\
\
                    # Modifie les champs $ConversationId et $MessageID par des valeurs uniques\
                    conversation_id_elem = find_element_by_xpath(root, ".//ConversationId")\
                    if conversation_id_elem is not None:\
                        new_conversation_id = f"$conversationId-\{count:011d\}"\
                        conversation_id_elem.text = new_conversation_id\
                        print(f"ConversationId modifi\'e9 -> \{new_conversation_id\}")\
\
                    message_id_elem = find_element_by_xpath(root, ".//MessageID")\
                    if message_id_elem is not None:\
                        new_message_id = f"$messageId-\{count:011d\}"\
                        message_id_elem.text = new_message_id\
                        print(f"MessageID modifi\'e9 -> \{new_message_id\}")\
\
                    # Supprime les pr\'e9fixes de namespaces, garde les namespaces implicites\
                    remove_namespace_prefixes(root)\
\
                    # Cr\'e9e le nouveau nom de fichier avec un suffixe unique pour chaque duplication\
                    new_file_name = file_name.replace('.xml', f'_new\{duplicate_num\}.xml')\
                    new_file_path = os.path.join(output_folder, new_file_name)\
                    \
                    # \'c9crit dans le nouveau fichier en conservant le namespace\
                    tree.write(new_file_path, encoding="utf-8", xml_declaration=True)\
                    print(f"Fichier modifi\'e9 et dupliqu\'e9 enregistr\'e9 sous : \{new_file_path\}")\
\
            except ET.ParseError as e:\
                print(f"Erreur de parsing dans le fichier \{file_name\}: \{e\}")\
\
# Exemple d'utilisation :\
folder_path = '/chemin/vers/le/dossier'  # Remplacez par le chemin de votre dossier contenant les fichiers XML\
output_folder = '/chemin/vers/dossier/sortie'  # Dossier o\'f9 enregistrer les fichiers modifi\'e9s\
\
# Liste des chemins XPath des champs \'e0 modifier (sans namespace ici)\
field_paths = [\
    './/Message/MirroredTrade/Trade/Instrument/SEDProduct/FlowPayoff/SwapReference/ExternalId',\
    './/Message/MirroredTrade/Trade/Instrument/SEDProduct/FlowPayoff/SwapReference/OtherField',\
]\
\
# Appel de la fonction avec duplication de 5 fois chaque fichier XML\
update_fields_in_folder(folder_path, field_paths, base_value="StressTestEBS", start_value=1, output_folder=output_folder, num_duplicates=5)\
}